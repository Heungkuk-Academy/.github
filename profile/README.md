# Heungkuk-Academy

흥국생명 연수원 예약 관리 시스템을 만드는 조직입니다.
연수원 시설 예약과 운영 업무를 웹에서 처리할 수 있도록 API 서버와 웹 프론트엔드, 배포 설정을 레포지토리별로 관리합니다.

## 레포지토리 구조



| 레포 | 설명 | 기술 | 공개 |
|---|---|---|---|
| [academy-backend](https://github.com/Heungkuk-Academy/academy-backend) | API 서버. 예약·계정·설문·엑셀 문서 생성 | Spring Boot, Java 21, JPA | 공개 |
| [academy-frontend](https://github.com/Heungkuk-Academy/academy-frontend) | 웹 프론트엔드 | Next.js, TypeScript | 공개 |
| academy-infra | 배포 설정과 운영 문서 (compose, nginx, 로그 수집) | Docker Compose, nginx, Loki | 비공개 |
| [academy-docs](https://github.com/Heungkuk-Academy/academy-docs) | 기획·API·ERD 등 프로젝트 문서 | Markdown | 공개 |

## 작업 규칙

1. **이슈 생성** — Feature / Bug / Chore 템플릿 사용
2. **브랜치 생성** — `develop`에서 `<type>/<설명>` 으로 분기 (예: `feat/reservation-search`)
3. **PR 생성** — 대상은 `develop`, PR 템플릿 작성. CI(빌드·테스트)가 통과해야 머지
4. **머지** — `develop`에 머지되면 **테스트 서버에 자동 배포**
5. **릴리스** — `develop` → `main` PR을 머지하면 **운영 서버에 자동 배포**

| 브랜치 | 용도 | 배포 대상 |
|---|---|---|
| `main` | 운영 | 운영 서버 |
| `develop` | 개발 기준 | 테스트 서버 |
| `<type>/<설명>` | 작업 | 배포 없음 |

- `main`과 `develop`에는 직접 커밋하지 않고 PR로만 반영합니다.
- 문서(`*.md`)만 바꾼 변경은 배포가 실행되지 않습니다.
- 배포는 backend · frontend 레포에서 자동으로 이루어집니다. 인프라(`academy-infra`) 설정 변경은 서버에서 수동으로 반영합니다.

## Git 형식

### 브랜치 이름

`<type>/<설명>` — 소문자와 하이픈을 사용합니다.

```
feat/reservation-search    fix/reservation-date    docs/readme    chore/gitignore
```

### 커밋 메시지

`<type>: <변경 내용>` 형식(Conventional Commits)을 따릅니다.

```
feat: 예약 목록 검색 기능 추가
fix: 예약 날짜가 하루 어긋나는 문제 수정
```

| type | 용도 |
|---|---|
| `feat` | 기능 추가 |
| `fix` | 버그 수정 |
| `docs` | 문서 |
| `refactor` | 구조 개선 (동작 변경 없음) |
| `test` | 테스트 추가·수정 |
| `ci` | CI · 배포 워크플로 |
| `chore` | 설정, 빌드, 기타 |

## 시작하기

각 레포의 README에 로컬 실행 방법과 환경 설정이 있습니다.
[academy-backend](https://github.com/Heungkuk-Academy/academy-backend#readme) ·
[academy-frontend](https://github.com/Heungkuk-Academy/academy-frontend#readme)
