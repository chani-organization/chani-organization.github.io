# Repository

이 저장소에는 입력한 텍스트를 기반으로 픽셀 아트를 생성해 주는 간단한 웹 페이지가 포함되어 있습니다. [index.html](./index.html)은 사용자가 입력한 문장을 LLM([Transformers.js](https://github.com/xenova/transformers.js) 이용)으로 5단계 분석/생성 파이프라인에 전달하고, `size`, `palette`, `data` 필드를 가진 24×24 픽셀 템플릿을 받아와 렌더링합니다.

## 모델 및 하드웨어 대응

- 우선 시도 모델: `HuggingFaceTB/SmolLM2-1.7B-Instruct` (약 1.7B 파라미터, 8K 컨텍스트). WebGPU 환경에서는 `fp16`으로, WASM/CPU 환경에서는 `auto` 정밀도로 로딩을 시도합니다. CPU 환경에서는 초기화에 수 분이 걸릴 수 있으니 로딩 진행률을 확인해 주세요.
- 로드 실패 시 자동 폴백: `onnx-community/Phi-3-mini-4k-instruct-q4f16` (약 4K 토큰 윈도우, int4/float16 혼합 양자화). 초기화 실패 메시지와 함께 폴백 여부를 로그에 안내합니다.
- 프롬프트 길이는 환경에 따라 600~900자로 가이드합니다. GPU(WebGPU) 사용 시 900자, CPU(WASM) 사용 시 600자를 넘기면 입력을 분할하도록 안내합니다.

## 파일 구성

- `index.html`: 사용자 인터페이스, 모델 로더, 5단계 대화 로직 및 캔버스 렌더링을 포함합니다.
- `_config.yml`: GitHub Pages용 기본 블로그 설정입니다.

## 실행 방법

브라우저에서 `index.html`을 열면, 텍스트 입력 후 **Generate** 버튼을 통해 5단계 LLM 대화가 실행되고 캔버스에 픽셀 아트 템플릿이 표시됩니다. 로그 영역과 브라우저 콘솔에서 단계별 진행 상황과 토큰 추정치를 확인할 수 있습니다.

