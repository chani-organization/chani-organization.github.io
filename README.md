# Repository

이 저장소에는 입력한 텍스트를 기반으로 픽셀 아트를 생성해 주는 간단한 웹 페이지가 포함되어 있습니다. [index.html](./index.html)은 사용자가 입력한 문장을 LLM([Transformers.js](https://github.com/xenova/transformers.js) 이용)으로 5단계 분석/생성 파이프라인에 전달하고, `size`, `palette`, `data` 필드를 가진 24×24 픽셀 템플릿을 받아와 렌더링합니다.

## 모델 및 하드웨어 대응

- WebGPU가 감지되면 `onnx-community/TinyLlama-1.1B-Chat-v1.0`(q4) 모델을 우선 시도해 더 긴(약 2K 토큰) 컨텍스트를 제공합니다.
- WebGPU 로딩에 실패하거나 GPU가 없으면 `onnx-community/ettin-decoder-150m-ONNX` 모델(q4/q8)을 자동으로 사용해 GTX 1050 급 환경에서도 무리 없이 동작하도록 구성되어 있습니다.
- 프롬프트 길이는 기본적으로 700~1100자 사이로 제한하며, 초과 시 분할 입력을 안내합니다.

## 파일 구성

- `index.html`: 사용자 인터페이스, 모델 로더, 5단계 대화 로직 및 캔버스 렌더링을 포함합니다.
- `_config.yml`: GitHub Pages용 기본 블로그 설정입니다.

## 실행 방법

브라우저에서 `index.html`을 열면, 텍스트 입력 후 **Generate** 버튼을 통해 5단계 LLM 대화가 실행되고 캔버스에 픽셀 아트 템플릿이 표시됩니다. 로그 영역과 브라우저 콘솔에서 단계별 진행 상황과 토큰 추정치를 확인할 수 있습니다.

