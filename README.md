# opensw23-limitless

## Team Introduction
허준호 201911291 Team Leader <br/>
조하상 202012784 Analyst <br/> 
김경민 202114216 Presentation manager <br/>
정원석 201911280 Github manager <br/>

## Topic Introduction
[Image Super Resolution]<br/>
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

=> 이중에서 저희가 사용하는 오픈소스는 **EDSR과 MDSR**을 제공합니다.<br/>
=>그러나 현재는 버전 이슈 (특히 torch.utils.data.dataloader)로 인해 MDSR기능을 일시적으로 이용할 수 없습니다.
=> EDSR은 MDSR보다 더 높은 품질의 이미지를 생성할 수 있지만 더 많은 계산 능력을 필요로 합니다.<br/>
  
## Results
저희는 총 10개의 data set을 분석하였습니다.<br/>
그 중 가장 EDSR 보간법을 잘 나타냈다고 생각이 되는 이미지를 대표 result로 선정하였습니다.<br/>

![image](https://github.com/S3ywa1k2r/opensw23-limitless/assets/127181452/d1b1ddee-872c-410d-8be6-96548bb2079c)


## Analysis/Visualization

저희는 **원본이미지**와 **원본 이미지에서 픽셀을 1/4 한 이미지에 bicubic interpolation, EDSR을 각각 적용**한 이미지를 비교하여 어떤 알고리즘이 더 원본에 가깝게 보간을 할 수 있는지 알아보고자 분석하였습니다.
저희는 결과물에 PSNR 수치값을 계산하여 나타내었는데 PSNR은 최대 신호 대 잡음비(Peak Signal-to-noise ratio)로 이미지 품질 측정의 기준중 하나입니다.
PSNR 수치는 생성 혹은 압축된 영상 또는 이미지의 화질에 대한 손실 정보를 평가하는 척도로, 일반적으로 PSNR 수치가 높을수록 손실이 적은, 즉 화질이 높은 것으로 알려져 있습니다. 그러나, PSNR은 인간이 시각적으로 느끼는 품질 차이를 표현한 방법이 아니기에 값이 높게 나와도 사람의 눈으로 보았을 때는 PSNR이 더 작게 나온 이미지가 화질이 더 좋아 보일 수도 있습니다. 저희는 이 부분을 직접 확인해보고자 **원본**과 **bicubic interpolation을 적용한 이미지**와 , **EDSR을 적용한 이미지**를 육안으로 비교해보았습니다. 여러 이미지를 적용해서 확인해 본 결과, 원본 이미지가 어떤 것인지에 따라 다른 결과가 도출되었습니다. <br/>


![image](https://github.com/S3ywa1k2r/opensw23-limitless/assets/127181452/3e8696f7-e428-45dc-85bf-69cdaff396f8) <br/>
위 사진은, 육안으로는 원본과 크게 다르지 않게 느껴질 수 있습니다. 그래서 동일한 사진의 특정부분을 확대해보았습니다. <br/>


![image](https://github.com/S3ywa1k2r/opensw23-limitless/assets/127181452/817aefb8-6b7d-44d1-b57c-cab3a90969dd) <br/>
사진을 확대해서 보면 확실하게 차이를 느낄 수 있습니다. 몇몇 조원은 EDSR을 적용한 사진이 조금 더 선명하고, 좋은 품질이라고 느낀 팀원도 있었습니다. <br/>

![image](https://github.com/S3ywa1k2r/opensw23-limitless/assets/127181452/b4b0d919-d1da-4f32-86f1-1ace5cfdefbe) <br/>
위 사진의 경우에는 bicubic, EDSR 모두 무언가 부자연스럽게 보입니다. bicubic을 적용한 사진은 흐릿한 느낌이 들고, EDSR을 적용한 사진은 수채화로 그린듯한 느낌이 듭니다. <br/>

<br/>
어떤 이미지는 셋 다 크게 차이가 없다고 느껴지는 경우도 있었고, 어떤 이미지는 깔끔하게 higher resolution이 적용된것이 있었고, 뿌옇게 보인다던가 이미지가 깨지는 듯한 느낌이 들어 보간이 제대로 잘 안된 이미지들도 있었습니다. 어떤 이미지의 PSNR 수치는 bicubic을 적용한 이미지가 EDSR을 적용한 이미지보다 미세하게 높았지만, 대부분의 사진에 대해 육안으로 느끼는 품질은 EDSR을 적용한 이미지가 bicubic을 적용한 이미지보다 훨씬 좋아보인다는 의견이 지배적이었습니다. 저희는 이러한 결과가 나온 이유가 각 알고리즘의 특성때문이라고 판단하였습니다. bicubic을 적용한 이미지들은 대체적으로 흐릿한 느낌이 들었고, EDSR을 적용한 이미지는 인위적으로 선명하게 만든 느낌이 들었습니다. 흐릿한 사진보다는 선명하게 보이는 이미지를 더 품질이 좋은 사진이라고 대부분 여기기 때문에, EDSR을 적용한 이미지가 더 품질이 좋다고 느끼는것으로 저희는 판단했습니다.<br/>

**결론적으로, PSNR 수치는 참고만 할 뿐 맹신해서는 안되겠다는 것을 이번 프로젝트를 통해 깨달았습니다. 또한 EDSR을 이용한 보간법이 손실된 이미지를, 다른 알고리즘들에 비해 상대적으로 원본에 가깝게 잘 보간하는것으로 결론을 내릴 수 있었습니다.** <br/>




## Installation
실행환경 - 윈도우10 64비트 운영체제, Intel(R) Core(TM) i5-1035G7 CPU @ 1.20GHz 1.50 GHz
1. git bash로 들어가서 source Scripts/activate 명령어를 입력해서 가상환경에 접속 한 다음 해당 pip들을 설치한다.<br/>
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
3. clone한 EDSR-PyTorch 폴더 내부에 src/demo.sh에서 현재 주석처리가 해제 되어있는 줄을 주석처리하고 'Test your own images'라는 주석 밑에 있는 줄의 주석을 해제함(demo.sh 파일에서 32번째 줄) <br/>
<br/>  
4. git bash로 python 가상환경을 실행하고 git bash 내부에서 다운받은 clone한 EDSR-PyTorch 폴더 내부에서 src 폴더 내부로 이동.<br/>
<br/>
5. 테스트할 사진을 project/test 폴더 안에 넣기<br/>
<br/>
6. 이동한 다음 sh demo.sh 실행하기<br/>
<br/> 
7. 실행 결과 나온 사진은 experiment/test/results-Demo에서 확인 가능 (model을 따로 다운 받을 필요 없이, default로 EDSR x4 model을 다운로드 받아 적용되어 결과물을 만들어 낼 것이다) <br/>
<br/>
input:<br/> 

  ![0853x4](https://github.com/S3ywa1k2r/opensw23-limitless/assets/127181452/9c39c0a7-674c-4956-9a93-72e5a1c3d484)<br/>
output:<br/>

  ![0853x4_x4_SR](https://github.com/S3ywa1k2r/opensw23-limitless/assets/127181452/10ad7297-5a4a-4716-901d-6d81906010d8)<br/>


## Presentation
