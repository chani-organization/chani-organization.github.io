# Repository

이 저장소에는 입력한 텍스트를 기반으로 좌표를 계산해 픽셀 아트를 생성해 주는 간단한 웹 페이지가 포함되어 있습니다. [index.html](./index.html)은 [`transformers.js`](https://xenova.github.io/transformers.js/)의 제로샷 분류 모델을 사용하여 텍스트를 하트/나무/집 중 가장 어울리는 레이블로 분류한 뒤, 그에 해당하는 픽셀 좌표와 색상을 계산해 캔버스에 찍습니다. 이러한 방식은 [proper-pixel-art](https://github.com/KennethJAllen/proper-pixel-art)에서 영감을 받았습니다. `_config.yml` 파일로 기본 블로그 구성을 확인할 수 있습니다.
