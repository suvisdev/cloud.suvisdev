# com.ragwatson — 에이전트 안내

## Titanic 모듈 — 사용할 경로 (삭제·옛 경로 사용 금지)

| 역할 | 경로 |
|------|------|
| CSV 업로드 API | `POST /titanic/james/upload` → `james_router.py` |
| 입력 포트 (ABC) | `backend/apps/titanic/app/ports/input/james_use_case.py` |
| 업로드 유스케이스 | `backend/apps/titanic/app/use_cases/james_interactor.py` (`JamesUseCase` 구현) |
| 업로드 호출 흐름 | `james_router` → `JamesInteractor` → `james_repository` → `james_pg_repository` |
| 업로드 출력 포트 (ABC) | `backend/apps/titanic/app/ports/output/james_repository.py` |
| 업로드 DB | `backend/apps/titanic/adapter/outbound/pg/james_pg_repository.py` |
| 승객 조회 API | `GET /titanic/walter/passengers` → `walter_router.py` |
| 조회 입력 포트 (ABC) | `backend/apps/titanic/app/ports/input/walter_use_case.py` |
| 조회 유스케이스 | `backend/apps/titanic/app/use_cases/walter_interactor.py` (`WalterUseCase` 구현) |
| 조회 호출 흐름 | `walter_router` → `WalterInteractor` → `walter_reader` → `walter_pg_reader` |
| 조회 출력 포트 (ABC) | `backend/apps/titanic/app/ports/output/walter_reader.py` |
| 조회 DB | `backend/apps/titanic/adapter/outbound/pg/walter_pg_reader.py` |
| DTO | `backend/apps/titanic/app/dtos/james_dto.py`, `walter_dto.py` |

## Friday13th 인증 — login / signup 분리 (jason 경로 사용 금지)

| 역할 | 경로 |
|------|------|
| 로그인 API | `POST /friday13th/login/login` → `login_router.py` (로그인만) |
| 로그인 흐름 | `login_router` → `LoginInteractor` → `login_repository` → `login_pg_repository` |
| 로그인 입력 포트 (ABC) | `backend/apps/friday13th/app/ports/input/login_use_case.py` |
| 로그인 출력 포트 (ABC) | `backend/apps/friday13th/app/ports/output/login_repository.py` |
| 회원가입 API | `POST /friday13th/signup/signup` → `signup_router.py` |
| 회원가입 흐름 | `signup_router` → `SignupInteractor` → `signup_repository` → `signup_pg_repository` |

### 존재하지 않음 (참조하지 말 것)

- `/friday13th/jason/*`, `jason_router`, `JasonInteractor` (login/signup으로 이전됨)
- `backend/apps/titanic/app/walter_reader.py` (삭제됨)
- `backend/apps/titanic/app/use_cases/james_command.py` (삭제됨 — `james_interactor.py` 사용)
- `services/com.ragwatson.agora/...` (이 repo 아님)
- `docs/DevOps/Backend/mova-erd.mmd` (삭제됨 — Mermaid는 `MOVA_ERD.md` 내부 블록)
