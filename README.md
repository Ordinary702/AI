# Nvidia AI Specialist Certification

# Title

[주제]

카메라와 인공지능을 활용한 비행물체 식별

---

**Aircraft identification using cameras**

# Opening background information

[ 배경 정보 ]

<aside>
✅ 최근 러시아, 우크라이나 전쟁에서 드론, 각종 비행 물체가 전장에 투입되는 모습을 볼 수 있다. 전장에는 이러한 레이더 시스템의 보급이 크게 활성화 되지 않아서 피해를 많이 볼 수 있다. 이러한 환경속에서 카메라와 인공지능 시스템을 활용하여 비싼 레이더 장비가 없어도 비행물체의 식별이 가능하게끔 한다.

</aside>

---

- In the recent wars between Russia and Ukraine, we can see drones and various flying objects being deployed on the battlefield. Since these radar systems are not widely distributed on the battlefield, a lot of damage can occur. In this environment, cameras and artificial intelligence systems are used to enable identification of flying objects without expensive radar equipment.

# General description of the current project

[프로젝트 전반적인 설명]

<aside>
✅ 카메라를 활용해 전투기, 비행물체의 움직임을 포착한다. 포착된 비행물체는 AI를 통해 분석 후 감지한다.

</aside>

---

- The camera captures real-time dynamic movements such as takeoff, landing, and gliding of fighter jets. This data is then used for detection utilizing AI.

### **Proposed idea for enhancements to the project**

[제안하고 싶은 프로젝트의 강점]

<aside>
✅ 전쟁에 드론 투입이 많아진만큼 비행물체를 빠르게 감지해 군인들의 생명을 지키는 데 도움이 될 수 있도록 한다.

</aside>

---

- As the use of drones in war increases, we can quickly detect flying objects to help protect the lives of soldiers.

### Value and signifiance of the project

[ 프로젝트의 중요성] 

<aside>
✅ 카메라와 인공지능을 활용하여 비행물체를 탐지, 분석하고, 식별하여 위험을 감지 혹은 신호를 보낼 수 있도록 하고 그에 따른 방어체계 활성화, 대피등을 할 수 있도록 한다.

</aside>

---

- Cameras and artificial intelligence are used to detect, analyze, and identify flying objects to detect or signal danger and activate defense systems and evacuate accordingly.

### **Current limitations**

[직면하고 있는 한계]

<aside>
✅ 먼거리에서 아군 전투기, 적군 전투기의 식별이 되지 않는 점, 레이더와 센서에 비해 식별 가능 거리가 짧다는 단점, 새도 비행물체로 인식될 수 있다는 문제점이 있다.

</aside>

---

- It has the disadvantage of not being able to identify friendly fighters and enemy fighters from a distance, the short identification distance compared to radar and sensors, and the problem that even birds can be recognized as flying objects.



인공지능이 인식한 비행물체
Flying object recognized by Yolov5

![KakaoTalk_Photo_2024-11-15-12-39-01_002](https://github.com/user-attachments/assets/78a3f9db-0ddf-4626-a640-a0f7bf975317)


## 영상 취득 방법:

- **인공지능 영상 취득 :** 대한민국 블랙이글스 팀의 에어쇼를 방문하면서 찍은 영상을 토대로 전투기를 비행물체로 인식시키게끔 영상을 취득합니다.
- **Artificial intelligence video acquisition:** Based on the video taken while visiting the Korea Black Eagles team's air show, video is acquired to recognize the fighter jet as a flying object.

1. **DarkLabel** 
- **데이터 추출**: 수집한 영상을 **DarkLabel** 에서 이미지로 추출합니다.
- **Data Extraction**: Extract the collected video as an image from **DarkLabel**.

[DarkLabel2.4.zip](https://github.com/user-attachments/files/17770051/DarkLabel2.4.zip)


<img width="1119" alt="Screenshot_2024-11-15_at_1 03 32_PM" src="https://github.com/user-attachments/assets/217329b6-6e44-4694-a6c6-0d61dc0eecf9">


영상이 해상도와 다르면  맞게 잘라줍니다.
If the video resolution is different, it will be cropped to fit.

[https://www.vapshion.com/vapshion4/download.php](https://www.vapshion.com/vapshion4/download.php)


<img width="1512" alt="Screenshot_2024-11-15_at_12 45 07_PM" src="https://github.com/user-attachments/assets/3b329d00-6aa3-4881-9604-027135c713d5">

640x640 해상도에 맞게 영상을 잘라서 저장해줍니다.
Cut and save the video to 640x640 resolution.

ZIP 파일을 압축해제하고  YAML파일을 열어서 추출할 내용들의 클래스를 추가해줍니다.
Unzip the ZIP file, open the YAML file, and add the classes for the contents to be extracted.

<aside>
💡 Plane_classes: ['Plane']

</aside>

<aside>
💡 format9:    # bird detection yolo (predefined format]
fixed_filetype: 1                 # if specified as true, save setting isn't changeable in GUI
data_fmt: [classid, ncx, ncy, nw, nh]
gt_file_ext: "txt"                 # if not specified, default setting is used
gt_merged: 0                    # if not specified, default setting is used
delimiter: " "                     # if not spedified, default delimiter(',') is used
classes_set: "Plane_classes"     # if not specified, default setting is used
name: "Plane"           # if not specified, "[fmt%d] $data_fmt" is used as default format name

</aside>

클래스 파일과 format 파일

<img width="208" alt="Screenshot_2024-11-15_at_12 46 59_PM" src="https://github.com/user-attachments/assets/812e97b5-e5c5-4159-ac74-5bc42603dda5">

<img width="216" alt="Screenshot_2024-11-15_at_12 47 27_PM" src="https://github.com/user-attachments/assets/b08bae52-e4c1-439f-bb40-905360f6e8fb">

Open Video : 원하는 영상, 사진을 불러옵니다.

Open Image Folder : 여러 장의 사진이 담긴 폴더를 불러옵니다.

0.pascal voc의 select bar : Formatting 형식을 지정한다. 여기서 자신이 라벨링할 클래스 이름을 선택할 수 있습니다.


2. **영상 이미지로 추출하는 방법**

'Open Video'를 눌러 추출할 영상을 선택 해줍니다.
Click ‘Open Video’ to select the video you want to extract.

<img width="1157" alt="Screenshot_2024-11-15_at_12 49 42_PM" src="https://github.com/user-attachments/assets/e5a31a89-dead-4915-9624-29a58cd8b976">


영상을 열고 추출할 이미지를 저장할 파일을 만들고 이미지를 추출해줍니다.
Open the video, create a file to save the image to be extracted, and extract the image.

<img width="1491" alt="Screenshot_2024-11-15_at_12 50 52_PM" src="https://github.com/user-attachments/assets/2f006b7c-1eac-4d26-8cc9-1c8cb5b6a75a">

Box + Label 을 체크해주고 ‘Plane’을 라벨링 해줍니다.
Check Box + Label and label ‘Plane’.

<img width="1489" alt="Screenshot_2024-11-15_at_12 51 50_PM" src="https://github.com/user-attachments/assets/5601e67e-5d01-4662-a763-4f3868746efb">


# 학습

<img width="1152" alt="Screenshot 2024-11-15 at 2 37 35 PM" src="https://github.com/user-attachments/assets/eb3c6855-ab45-4a4e-85aa-19da6a9bef0b">

파일경로를 인식할 수 있게 수정을 해줍니다.
Modifies the file path to recognize it.

yolov5에 필요한 필수 파일을 설치합니다.
Install the required files required by yolov5.

<img width="1156" alt="Screenshot 2024-11-15 at 2 40 38 PM" src="https://github.com/user-attachments/assets/229f44a9-3708-4540-aa6b-b787a9f9faa7">

라벨링한 텍스트파일, 이미지파일을 저장할 Train 과 Val 폴더를 생성하고 ,이미지를 관리합니다.
Create Train and Val folders to store labeled text files and image files, and manage the images.

<img width="1163" alt="Screenshot 2024-11-15 at 2 42 20 PM" src="https://github.com/user-attachments/assets/2afc4d14-5172-4c2b-ab22-d6ede33b9106">
<img width="1149" alt="Screenshot 2024-11-15 at 2 43 26 PM" src="https://github.com/user-attachments/assets/731619b1-ecb9-4b26-9ecb-6ccd0a7070b5">


학습을 시작합니다.
Start learning.

<img width="1150" alt="Screenshot 2024-11-15 at 2 47 49 PM" src="https://github.com/user-attachments/assets/fbb342c6-5614-4958-a4b3-2e275998a73d">

학습이 완료되면 검증을 위해 원본 혹은 샘플 영상을 넣고 실행합니다. yolov5안에 Sample이란 경로를 만들어 그 안에 원본 영상 혹은 샘플 영상을 넣고 검증을 하도록 하였습니다.
Once learning is complete, insert the original or sample video and run it for verification. I created a path called Sample in yolov5, inserted the original video or sample video into it, and verified it.

샘플 검증 영상
Sample analysis video
https://youtu.be/JtBp5diGqwM?si=DhiRnz5bqqJ-RfuN

Google Drive Yolov5 파일
Google Drive Yolov5 File
https://drive.google.com/drive/folders/1_5Gn8RFA9cj1nZTnByMXxV-LyWLjM37U?usp=sharing
