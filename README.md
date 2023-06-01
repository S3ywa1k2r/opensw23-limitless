# opensw23-limitless

## Team Introduction
허준호 201911291 Team Leader <br/>
조하상 202012784 Coder <br/> 
김경민 202114216 Coder <br/>
정원석 201911280 Github manager <br/>

## Topic Introduction
<Image Super Resoltion>
Image Super Resolution은 저해상도 이미지를 고해상도 이미지로 변환하는 기술입니다.<br/>
딥러닝이 적용되면서 급격히 발전하였으며, 이제는 저해상도 이미지를 고해상도로 변환하여도 인간의 눈으로 구별할 수 없을 정도로 높은 품질의 이미지를 생성할 수 있습니다.<br/>
Image Super Resolution은 다양한 분야에서 활용될 수 있는데, 예를 들어, 저해상도 카메라로 촬영된 이미지를 고해상도로 변환하여 더 선명한 이미지를 얻을 수 있고, 옛날에 촬영된 이미지를 고해상도로 변환하여 디지털화할 수 있습니다. 또한, 이미지 슈퍼 리졸루션은 의료 분야에서 의료 이미지의 해상도를 높이는 데에도 사용될 수 있습니다.<br/>

이미지 슈퍼 리졸루션을 수행하는 방법에는 여러 가지가 있습니다. 가장 일반적인 방법은 '보간법(Interpolation)'을 사용하는 것입니다. 보간법은 저해상도 이미지의 픽셀값을 사용하여(픽셀값은 하나의 행렬 형태로 변환되어 사용됩니다) 고해상도 이미지의 픽셀값을 추정하는 방법입니다. 보간법은 간단하고 빠르게 이미지의 해상도를 높일 수 있지만, 고품질의 이미지를 생성하는 데에는 한계가 있습니다.<br/>

**딥러닝을 이용한 Image Super Resolution**은 보간법보다 더 높은 품질의 이미지를 생성할 수 있습니다. 딥러닝은 저해상도 이미지와 고해상도 이미지의 쌍을 학습하여 저해상도 이미지에서 고해상도 이미지를 생성합니다.<br/>
  
-딥러닝을 이용한 Image Super Resolution 알고리즘의 종류는 대표적으로 다음과 같습니다.<br/>  
**VDSR(Very Deep Super Resolution)<br/>
SRCNN(Super-Resolution Convolutional Neural Network)<br/>
DnCNN(Denoising Diffusion Model for Super-Resolution)<br/>
EDSR(Enhanced Deep Super Resolution)<br/>
ESRGAN(Enhanced Super Resolution Generative Adversarial Network)<br/>
MDSR(Multi-scale Densely Residual Networks)**<br/>

=> 이중에서 우리가 사용하는 오픈소스는 **EDSR과 MDSR**을 제공합니다.<br/>
=>그러나 현재는 버전 이슈 (특히 torch.utils.data.dataloader)로 인해 MDSR기능을 일시적으로 이용할 수 없습니다. 만약 MDSR 모델을 사용하고싶다면, 이전 버전의 branch를 이용해야합니다.<br/>
=> EDSR은 MDSR보다 더 높은 품질의 이미지를 생성할 수 있지만 더 많은 계산 능력을 필요로 합니다.<br/>
  
## Results
  
원본이미지<br/>
![0853x4](https://github.com/S3ywa1k2r/opensw23-limitless/assets/127181452/917b6b20-c1ca-4be9-aa30-3f6ff49599ba)<br/>
파일 크기: 268KB<br/>
사진 크기: 510 x 339<br/>
<br/>  
적용이미지<br/>
![0853x4_x4_SR](https://github.com/S3ywa1k2r/opensw23-limitless/assets/127181452/a3839d4d-790d-4722-a0bd-75ab7ed7d7ba)<br/>
파일 크기: 2.53MB<br/>
사진 크기: 2040 x 1356<br/>
<br/>  
## Analysis/Visualization

## Installation
실행환경1 - 윈도우10 64비트 운영체제, Intel(R) Core(TM) i5-1035G7 CPU @ 1.20GHz 1.50 GHz
1. git bash로 들어가서 가상환경에 접속 한 다음 해당 pip들을 설치한다.<br/>
Pytorch 설치 - pip install torch<br/>
numpy 설치 - pip install numpy<br/>
skimage 설치 - pip install scikit-image<br/>
imageio 설치 - pip install imageio<br/>
matplotlib 설치 - pip install matplotlib<br/>
tqdm 설치 - pip install tqdm<br/>
cv2 설치 - pip install opencv-python<br/>
<br/>
2. https://github.com/sanghyun-son/EDSR-PyTorch<br/>
이 페이지의 README.md에서 나온 code 주소로 git clone하기<br/>
-> git clone https://github.com/thstkdgus35/EDSR-PyTorch<br/>
<br/>
3. https://cv.snu.ac.kr/research/EDSR/model_pytorch.tar <br/>
  위 링크를 클릭하여 model 파일을 다운 받아서, 다운 받은 파일을 EDSR-PyTorch/experiment/model 경로에  넣기<br/>
<br/>
4. src/demo.sh에서 현재 주석처리가 해제 되어있는 줄을 주석처리하고 'Test your own images'라는 주석 밑에 있는 줄의 주석을 해제함(demo.sh 파일에서 32번째 줄) <br/>
<br/>  
5. git bash로 python 가상환경을 실행하고 git bash 내부에서 다운받은 clone한 EDSR-PyTorch 폴더 내부에서 src 폴더 내부로 이동, 이동한 다음 sh demo.sh 실행하기<br/>
<br/> 
6. 실행 결과 나온 사진은 experiment/test/results-Demo에서 확인 가능<br/>
<br/>
input:<br/> 
![0853x4](https://github.com/S3ywa1k2r/opensw23-limitless/assets/127181452/99d61970-53b7-4c0f-bd9b-b7bda316e51c)<br/>
output:<br/> 
![0853x4_x4_SR](https://github.com/S3ywa1k2r/opensw23-limitless/assets/127181452/184b613f-41d0-479b-8fa2-4b1159dba1dc)<br/>  
  
## Presentation
