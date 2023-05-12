# DETR
AI특론 과제

코드 출처: https://github.com/facebookresearch/detr

## Requirements
저의 경우에는 gpu 서버를 가지고 conda 가상환경을 만들어서 이용했습니다.

python 3.9, torch=1.11.0, torchvision=0.12.0을 설치하였고, (다른 버전의 torch와 torchvision을 설치한 결과, 코드가 작동하지 않았습니다.) 
````
conda install -c conda-forge pycocotools
conda install cython scipy
````
또한, 위의 코드를 이용해서 pycocotools와 cython, scipy를 설치해 주었습니다.

## Data preparation
COCO 2017 Dataset을 이용했습니다.

![image](https://github.com/kimsy9587/DETR/assets/131329056/b7eeb163-cde8-4d2c-ae37-659b314d4701)

위의 사진대로 coco 디렉토리를 만들어서 COCO Dataset을 구성했습니다.

## Training
![image](https://github.com/kimsy9587/DETR/assets/131329056/248fb232-7e12-456d-a385-6231f50f0948)
서버에 output 디렉토리를 만들고 경로를 지정해 줬습니다. 

![image](https://github.com/kimsy9587/DETR/assets/131329056/2ebca0fd-6b23-4328-a2b6-dd5b3499a528)
dataset의 용량이 커서 epoch을 13까지밖에 못 돌렸는데 이런 결과값이 나왔습니다.

![image](https://github.com/kimsy9587/DETR/assets/131329056/2f0754b7-9e3d-40ed-b2ed-5840a9af4986) 
또한 output 디렉토리에 checkpoint.pth가 저장이 됩니다.

## Evaluation
````
python main.py --batch_size 2 --no_aux_loss --eval --resume checkpoint.pth --coco_path /path/to/coco
````
main.py, checkpoint.pth, coco_path의 경로를 설정해 주어야 합니다.

![image](https://github.com/kimsy9587/DETR/assets/131329056/175275c3-58d8-4f3c-9777-6caed347bda5)
![image](https://github.com/kimsy9587/DETR/assets/131329056/23c6ab18-89cc-43fc-8c20-d14a3ef92d48)
저는 위의 사진과 같은 결과가 나왔는데 왜 이런 결과가 나왔는지, 이 결과가 괜찮은 결과인지 파악해 볼 예정입니다.
