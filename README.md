# ConfTrack (before-aoe)

학회 마감일과 내 투고 계획을 함께 관리하는 웹 서비스입니다.
Vision · AI/ML · Robotics · Graphics 분야 20개 학회의 마감일을 AoE/KST 기준 D-day로 보여 주고,
"논문 A → 학회 B" 투고 계획을 준비부터 결과까지 상태별로 관리합니다.

## 기술 스택

| 영역 | 사용 기술 |
|---|---|
| 프런트엔드 | React 19, TypeScript, Vite, React Router, Tailwind CSS |
| 인증·데이터 | Firebase Authentication, Cloud Firestore |
| 테스트 | Vitest |
| CI | GitHub Actions (lint → test → build) |
| 배포 | JCloud |

## 로컬 실행

Node.js 22 이상이 필요합니다 (`.nvmrc` 기준 26).

```bash
npm install      # 의존성 설치
npm run dev      # 개발 서버 (http://localhost:5173)
npm test         # 단위 테스트
npm run lint     # 린트
npm run build    # 프로덕션 빌드 (dist/)
```

## 폴더 구조

```
src/
  domain/     도메인 규칙 (마감일·시간대, 투고 상태)
  services/   서비스 계층 (투고 처리, 명령, 검증)
  data/       저장소 (Firestore / InMemory)
  infra/      Firebase 인증 어댑터, 이벤트 버스
  ui/         화면 (pages, components, hooks)
scripts/sync/ 학회 데이터 동기화 (GitHub Actions에서 실행)
tests/unit/   단위 테스트
```

## 외부 자료 및 출처

| 항목 | 출처 | 라이선스 | 사용 방식 |
|---|---|---|---|
| 프로젝트 초기 뼈대 | [create-vite](https://github.com/vitejs/vite/tree/main/packages/create-vite) `react-ts` 템플릿 | MIT | 생성 후 데모 코드 제거 |
| 학회 마감 데이터 | [ccfddl/ccf-deadlines](https://github.com/ccfddl/ccf-deadlines) | MIT | 1순위 데이터 소스 (예정) |
| 학회 보조 정보 | [huggingface/ai-deadlines](https://github.com/huggingface/ai-deadlines) | MIT | 장소·회의 기간 보조 (예정) |
