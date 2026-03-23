# 폰트 서브셋 생성기 (Font Subset Generator)

이 프로젝트는 원본 폰트 파일(TTF)에서 필요한 글자(Glyphs)만 추출하여 웹 환경이나 앱에서 최적화된 용량으로 사용할 수 있는 서브셋 폰트들을 생성하는 도구입니다.

## 주요 특징
- **다양한 포맷 지원**: TTF, WOFF, WOFF2 포맷 자동 생성
- **글자 목록 기반 추출**: 별도의 텍스트 파일을 통해 추출할 글자(Glyphs)를 유연하게 관리
- **자동화 스크립트**: `generate.sh`를 통해 `fonts/` 디렉토리 내의 모든 폰트를 일괄 처리

## 설치 및 설정

### 1. 가상 환경 설정
Python 의존성을 관리하기 위해 가상 환경 사용을 권장합니다.
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
```

### 2. 패키지 설치
`requirements.txt`에 명시된 `fonttools` 및 압축 라이브러리들을 설치합니다.
```bash
pip install -r requirements.txt
```

## 사용 방법

### 1. 폰트 준비
원본 TTF 폰트 파일을 `fonts/` 디렉토리에 넣습니다. 현재 스크립트는 모든 `.ttf` 파일을 대상으로 동작합니다.

### 2. 글자 목록 정의
추출하고자 하는 글자들을 텍스트 파일로 준비합니다. 기본 설정은 `glyphs/TetraTheta-glyphs.txt`를 사용하도록 되어 있습니다. 필요 시 `generate.sh` 내의 `GLYPHS` 변수 값을 수정하십시오.

### 3. 스크립트 실행
터미널에서 다음 명령어를 실행합니다. (Windows의 경우 Bash를 지원하는 터미널(Git Bash 등)에서 실행 가능합니다)
```bash
./generate.sh
```

## 결과물 구조
스크립트 실행이 완료되면 `dist/` 디렉토리에 폰트 파일명으로 명명된 폴더가 생성되며, 그 안에 서브셋된 `ttf`, `woff`, `woff2` 파일들이 저장됩니다.

```text
dist/
└── [폰트이름]/
    ├── [폰트이름].ttf
    ├── [폰트이름].woff
    └── [폰트이름].woff2
```

## 주요 의존성
- [fonttools](https://github.com/fonttools/fonttools): 폰트 조작 및 서브셋 생성을 위한 핵심 라이브러리
- [Brotli](https://github.com/google/brotli): WOFF2 압축 지원
- [zopfli](https://github.com/google/zopfli): WOFF 압축 최적화
