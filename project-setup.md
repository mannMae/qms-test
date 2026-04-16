# AI Prompt: QMS Testing Project Setup

이 프롬프트는 GitHub 기반의 자동 QMS(Quality Management System) 프로세스를 테스트하기 위한 새로운 프로젝트를 구축하는 데 사용됩니다.

## 프로젝트 개요
- **목표**: `auto-qms-with-git` 액션(또는 스크립트)이 정상적으로 작동하는지 확인하기 위한 "더미 프로젝트" 구축.
- **핵심 기능**:
  1. Markdown 문서의 변경 감지.
  2. 문서 버전 자동 업데이트.
  3. 수정 이력(History) 자동 기록.
  4. PDF 문서 생성 및 출시(Release/Artifact).

## AI 지시 사항 (Requirements)

다음 요구사항에 맞춰 새 프로젝트를 구성해줘:

### 1. 프로젝트 구조 (Directory Structure)
```text
qms-test-app/
├── docs/               # QMS 관리 대상 문서 폴더
│   ├── SDP.md          # Software Development Plan (샘플)
│   └── SRS.md          # Software Requirements Specification (샘플)
├── .github/
│   └── workflows/
│       └── qms-verification.yml  # QMS 자동화 워크플로우
└── README.md           # 테스트 가이드
```

### 2. 샘플 문서 내용
- `docs/SDP.md`와 `docs/SRS.md` 파일에 간단한 QMS 헤더(문서번호, 초기 버전 0.1, 작성날짜 등)를 포함한 내용을 작성해줘.

### 3. GitHub Actions 설정
- `.github/workflows/qms-verification.yml` 파일을 작성해줘.
- 이 워크플로우는 `main` 또는 `test` 브랜치에 `docs/` 폴더 내 파일이 **push**될 때 실행되어야 해.
- 실행 단계:
  1. `checkout` (LFS 지원 포함).
  2. `auto-qms-with-git` 액션 호출 (또는 해당 프로젝트의 스크립트 실행).
  3. 생성된 PDF와 업데이트된 Markdown 파일을 커밋하거나 Artifact로 업로드.

### 4. 테스트 시나리오 가이드
- README.md에 다음 테스트 방법을 포함해줘:
  - "문서 본문 수정 후 Push -> 버전 번호가 0.1에서 0.2로 올라가는지 확인"
  - "History 섹션에 수정 사항이 자동으로 추가되는지 확인"
  - "PDF 파일이 `output/` 폴더에 생성되는지 확인"

---
**주의 사항**: 
- `auto-qms-with-git` 레포지토리의 경로를 참조할 수 있도록 `uses: <username>/auto-qms-with-git@main` 형태의 구문을 포함할 것.
- Git User Identity 설정(`git config user.name`, `user.email`)이 워크플로우 내에 포함되어 오류가 발생하지 않도록 할 것.
