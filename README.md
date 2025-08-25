# Repository

이 저장소에는 입력한 텍스트를 기반으로 픽셀 아트를 생성해 주는 간단한 웹 페이지가 포함되어 있습니다. [index.html](./index.html)은 사용자가 입력한 문장을 LLM(Xenova/distilgpt2 모델, [Transformers.js](https://github.com/xenova/transformers.js) 이용)에 전달해 `size`, `palette`, `data` 필드를 가진 JSON 템플릿을 받아오고, 이를 32×32 캔버스에 확대해 표시합니다.

`_config.yml` 파일로 기본 블로그 구성을 확인할 수 있습니다.

