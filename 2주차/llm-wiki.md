# LLM-Wiki 설치 및 초기화 가이드

이 문서는 에이전트를 위한 지식 저장소(Knowledge Base) 컴파일러인 **LLM-Wiki (`llm-wiki-compiler`)**를 설치하고 프로젝트 워크스페이스 내에 초기 위키 구조를 구성하는 방법에 대해 다룹니다. 에이전트가 수행한 실제 설치 및 초기화 로그를 바탕으로 작성되었습니다.

---

## 📋 사전 준비 사항

LLM-Wiki 컴파일러는 Node.js 환경에서 동작합니다. 설치를 진행하기 전에 로컬 환경에 아래 도구들이 설치되어 있는지 확인합니다.

- **Node.js** (v18 이상 권장)
- **NPM** (Node Package Manager)
- **Python 3** (종속성 빌드용)

> [!TIP]
> 터미널에서 아래 명령어를 실행하여 현재 설치된 개발 환경의 버전을 확인할 수 있습니다.
> ```bash
> node -v
> npm -v
> python3 --version
> ```

---

## 🛠️ 1단계. LLM-Wiki 설치 절차

에이전트는 아래와 같은 단계별 프로세스를 따라 패키지를 탐색하고 설치를 완료했습니다.

### 1. 기존 설치 상태 및 환경 점검
시스템에 이미 `llmwiki` CLI 도구가 설치되어 있는지 확인하고, 설치에 필요한 개발 환경(Node.js, npm, Python)이 정상 작동하는지 체크합니다.
```bash
# 기존 CLI 설치 여부 확인
command -v llmwiki || command -v llm-wiki

# 필수 런타임/패키지 매니저 버전 확인
node -v && npm -v && python3 --version
```

### 2. NPM 저장소 패키지 정보 검색
정확한 패키지명과 최신 버전을 조회하기 위해 NPM 저장소를 검색합니다. 실제 컴파일러 역할을 하는 **`llm-wiki-compiler`** 패키지를 찾아 설치 준비를 합니다.
```bash
# NPM 저장소 정보 조회
npm view llm-wiki-compiler name version description

# CLI 실행 파일(bin) 및 버전 정보 확인
npm view llm-wiki-compiler bin version
```

### 3. LLM-Wiki 컴파일러 로컬 설치
현재 프로젝트 워크스페이스 내에 `llm-wiki-compiler`를 종속성으로 설치합니다.
```bash
# 프로젝트 로컬에 패키지 설치
npm install llm-wiki-compiler
```

### 4. CLI 실행 및 도움말(Help) 테스트
설치가 완벽히 완료되었는지 검증하기 위해 로컬 바이너리 실행 파일(`./node_modules/.bin/llmwiki`)로 도움말 출력을 테스트합니다.
```bash
# 도움말 명령어 실행 테스트
./node_modules/.bin/llmwiki --help
```

### 📸 에이전트 설치 실행 로그

아래 이미지는 Hermes Agent가 실행 환경을 점검하고 `llm-wiki-compiler`를 탐색 및 설치하는 과정을 담은 실제 대화 로그입니다.

![LLM-Wiki 설치 실행 로그](../images/llm-wiki-install.png)

---

## ⚙️ 2단계. 위키 초기 세팅 및 구조 생성 (Initialization)

설치가 완료되면 워크스페이스 내에 에이전트가 읽고 쓸 수 있는 위키 폴더와 기본 템플릿 구조를 구축해야 합니다.

### 1. 위키 스키마 초기화 실행
설치된 컴파일러 CLI의 `schema` 명령어를 이용해 위키의 메타데이터 및 형식 규칙을 규정하는 스키마를 초기화합니다.


### 2. 기본 파일 및 폴더 구조 생성 확인
스키마 초기화가 완료되면 워크스페이스 내에 다음과 같은 핵심 구조가 자동 생성됩니다.
- **`wiki/` 폴더**: 실질적인 지식 문서가 관리되는 공간
- **`SCHEMA.md`**: 위키 작성 규칙 및 가이드라인 정의 파일
- **`index.md`**: 위키 페이지들의 색인(Index) 역할을 하는 메인 페이지
- **`log.md`**: 위키 업데이트 이력 및 작업 기록을 추적하는 변경 로그 파일
- **`schema.json`**: 메타데이터 유효성 검증용 JSON 스키마 파일


### 📸 에이전트 초기화 및 구조 생성 로그

아래 이미지는 에이전트가 설치 완료 후 `schema` 명령어 등을 사용하여 위키 스키마를 초기화하고 기본 구성을 세팅하는 실제 과정입니다.

![LLM-Wiki 초기 세팅 실행 로그](../images/llm-wiki-init.png)

---


