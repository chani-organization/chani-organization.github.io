# Repository

이 저장소에는 입력한 텍스트를 기반으로 픽셀 아트를 생성해 주는 간단한 웹 페이지가 포함되어 있습니다. [index.html](./index.html)은 사용자가 입력한 문장을 LLM([Transformers.js](https://github.com/xenova/transformers.js) 이용)으로 5단계 분석/생성 파이프라인에 전달하고, `size`, `palette`, `data` 필드를 가진 24×24 픽셀 템플릿을 받아와 렌더링합니다.

## 모델 및 하드웨어 대응

- GPU 지원 여부와 관계없이 `HuggingFaceTB/SmolLM2-1.7B-Instruct` 모델을 단일 옵션으로 로드합니다. WebGPU가 감지되면 GPU 가속으로, 그렇지 않으면 WASM 경로로 동일한 모델을 실행하되, 1.7B 파라미터 모델 특성상 WebGPU 사용을 권장합니다.
- 프롬프트 길이는 환경에 따라 600~900자 사이로 제한하며, 초과 시 분할 입력을 안내합니다.

## 파일 구성

- `index.html`: 사용자 인터페이스, 모델 로더, 5단계 대화 로직 및 캔버스 렌더링을 포함합니다.
- `_config.yml`: GitHub Pages용 기본 블로그 설정입니다.

## 실행 방법

브라우저에서 `index.html`을 열면, 텍스트 입력 후 **Generate** 버튼을 통해 5단계 LLM 대화가 실행되고 캔버스에 픽셀 아트 템플릿이 표시됩니다. 로그 영역과 브라우저 콘솔에서 단계별 진행 상황과 토큰 추정치를 확인할 수 있습니다.

