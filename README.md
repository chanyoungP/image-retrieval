# Image-Retrieval
이 레포지토리는 Fly Ai 프로젝트 "AI 도슨트 서비스 : Acent"에서 이미지 검색 기능을 구현한 것입니다.

### 기능 목적
미술관 전시회에서 관람객에게 콘텐츠를 더 쉽게 제공하기 위해서 vision base의 콘텐츠 제공을 안정적으로 만들기 위한 기능입니다.
미술관에서 사람들은 QR 코드로 콘텐츠를 제공받고 있습니다. 하지만, QR 코드의 경우 작품 가까이에 가서 사진을 찍어야하는 불편함이 있습니다.
이에, **멀리서 작품 사진으로 콘텐츠를 제공받을 수 있도록 하기위한 기능입니다.** 
또한 오프라인으로 콘텐츠를 제공하는 것이기 때문에, **각기 다른 각도와 조도에서 찍힌 작품이 DB에 사전 저장된 작품과 매칭을 시키기 위한 기능입니다.**

### 이미지 검색 과정
1. 사전 훈련된 신경망(e.g. ResNet, VGG)을 로드합니다.
2. 가중치를 동결합니다.
3. 헤더(FC)를 제거하고 이미지의 피쳐를 벡터화한 평면 레이어만 남깁니다.
4. 모든 DB에 있는 이미지를 계산하고 벡터화된 이미지를 JSON 파일로 얻습니다.
5. 입력 이미지를 계산하고 벡터화된 이미지를 얻습니다.
6. 각 벡터화된 이미지 간의 코사인 유사도를 계산합니다.
7. 후보 이미지 중 가장 유사한 이미지를 선택합니다.

### file 구조
├── README.md
├── dbimages
│   ├── 1.jpg
│   ├── 2.jpg
├── image_dict.json
├── models
│   ├── image_dict.json
│   ├── resnet50_model.pth
│   └── vgg16_model.pth
├── sample_input
│   ├── input_image.jpg
├── src
│   ├── ImageRetrieval.py
│   ├── myerror.py
│   └── myexception.py
├── test_retrieval.py
└── tool
    ├── model_save.py
    └── vectorize_db_image.py

### 결과 
<img width="907" alt="image" src="https://github.com/chanyoungP/image-retrieval/assets/67907678/6baa00b5-10c6-4064-97e5-37dc741bd6ee">
