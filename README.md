# QMS Testing Project

이 프로젝트는 `auto-qms-with-git` GitHub Action의 기능을 테스트하고 검증하기 위한 더미 프로젝트입니다.

## 프로젝트 구조
- `docs/`: QMS 관리 대상 Markdown 문서들이 저장된 폴더.
- `.github/workflows/`: QMS 자동화 워크플로우 설정 파일.
- `output/`: (워크플로우 실행 시 생성되는) PDF 파일 저장 경로.

## 테스트 시나리오

다음 단계에 따라 QMS 자동화 시스템을 테스트할 수 있습니다:

### 1. 버전 업데이트 및 이력 기록 테스트
- `docs/SDP.md` 또는 `docs/SRS.md` 파일의 **본문 내용**을 수정합니다.
- 변경 내용을 `main` 또는 `test` 브랜치에 **Push**합니다.
- **예상 결과**:
  - 문서 상단의 `Version` 정보가 `0.1`에서 `0.2`로 자동 업데이트됩니다.
  - `History` 테이블에 수정 사항이 자동으로 추가됩니다.

### 2. PDF 생성 확인
- GitHub Actions 탭에서 워크플로우가 성공적으로 완료되었는지 확인합니다.
- **예상 결과**:
  - `output/` 폴더에 해당 문서의 PDF 버전이 생성됩니다.
  - 생성된 PDF 파일은 GitHub Artifacts로 업로드됩니다.

## 주요 고려 사항
- 워크플로우는 `docs/` 폴더 내의 파일이 push될 때만 실행됩니다.
- Git Identity는 워크플로우 내에서 `Antigravity AI`로 설정되어 자동 커밋을 수행합니다.
