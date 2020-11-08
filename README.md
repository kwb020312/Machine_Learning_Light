# 빛반응 가상머신

https://www.youtube.com/user/egoing2

유튜브 생활코딩 참고,


teachablemachine.withgoogle.com

으로 접속해준다

<img src="./gitImages/started.PNG">

<img src="./gitImages/ImageProject.PNG">

해당 버튼을 누르게되면 아래와 같은 화면을 볼 수 있다.

<img src="./gitImages/TeachableMain.PNG">

Webcam 을 클릭하자
(캠이 없는경우 진행 불가능)

Hole to Record 버튼을 클릭할 경우 사진이 적용되며 여러장 적용시키는 편이 좋다

<img src="./gitImages/Class.PNG">

클래스를 수정해주는데 , 나의 경우는 깜깜한 화면과 밝은화면 즉 낮과 밤 으로 지정해주었다.

<img src="./gitImages/uploaded.PNG">

순차적으로 클릭 한 후

<img src="./gitImages/getCode.PNG">

모델을 업로드 하고 추출된 코드를 카피해주면 준비 끝

간단하게 폴더를 하나 만들어

index.html 을 만들어 준 후

```javascript
yarn init

yarn add local-web-server -global

// 터미널 재시작 후 실행가능

ws --https --port (포트번호) --open

// https 로 설정해 주어야만 웹에서 캠실행 가능 권한이 부여된다.
```

```html
<html>
    <body>
        (아까넣은 코드들)
    </body>
</html>
```

간단하게 코드를 정리하자면

<img src="./gitImages/StartWebCam.PNG">

해당 부분에서 웹캠실행을 해준다

<img src="./gitImages/result.PNG">

해당 부분에서 판정을 실행해주는데 

```javascript
const prediction = await model.predict(webcam.canvas)
// 에 아까 설정한 Class1 과 Class 2 가 각각 0번째 배열과 1번째 배열로 들어가있다.
// 값은 prediction[배열번호].probability 로 추출이 가능하며 이 때의 값은
// 얼마나 해당 상황과 일치해 있느냐 이다.
// 나의 경우 주변의 밝기를 Class 로 잡았기 때문에 아침에는 prediction[0] 이 크며
// 밤에는 prediction[1] 이 크게 설정된다
```

<img src="./gitImages/Loop.PNG">

해당 판정을 반복해서 실행해준다.

밤낮을 기다리기 힘들기 때문에 캠을 손가락으로 가린경우 밤 ,
아닌경우 낮 으로 설정되게 Model 을 잡아둔 후

손가락으로 가리지 않은경우 (낮)

<img src="./gitImages/day.PNG">

손가락으로 캠을 가린경우 (밤)

<img src="./gitImages/night.PNG">
