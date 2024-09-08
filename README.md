# Human-body-detection-security-system Public
2023 | Embedded Term Project

# Raspberry Pi를 사용한 임베디드 시스템 텀 프로젝트

## 프로젝트 개요

이 프로젝트는 Raspberry Pi와 다양한 센서를 활용하여 인체 감지 및 경비 시스템을 구축하는 임베디드 시스템 텀 프로젝트입니다. 인체 감지 모듈이 동작을 감지하면, LED와 부저가 작동하며, 카메라로 사진을 찍는 방식으로 작동합니다.

## 주요 기능

1. **인체 감지 및 경보**:
   - 인체 감지 모듈을 통해 움직임이 감지되면 LED가 깜빡이고 부저가 울립니다.
   - 카메라가 작동하여 사진을 찍고 현장의 상황을 기록합니다.

2. **Raspberry Pi GPIO 핀 구성**:
   - Raspberry Pi의 GPIO 핀을 활용하여 LED, 부저, 카메라 등 다양한 센서를 제어합니다.

3. **핵심 코드**:
   - 카메라 촬영: 인체 감지가 되면 파이썬 스크립트를 호출하여 카메라로 사진을 찍습니다.
   - LED 제어: LED를 켜고 끄는 동작을 반복하여 경고 표시를 합니다.

## 코드 예시

### (1) 카메라 촬영 코드
```cpp
void takePicture(void)
{
    printf("call python code
");
    system("python picam.py");
    system("raspistill -o img.jpg");
}
```

### (2) LED 제어 코드
```cpp
void redLedBlick(void)
{
    // LED ON
    digitalWrite(RGBLEDPOWER, 1);
    digitalWrite(RED, 1);
    digitalWrite(GREEN, 0);
    digitalWrite(BLUE, 0);
    
    delay(500);
    
    // LED OFF
    digitalWrite(RGBLEDPOWER, 0);
    digitalWrite(RED, 0);
    digitalWrite(GREEN, 0);
    digitalWrite(BLUE, 0);
    
    delay(500);
}
```

### (3) 메인 동작 코드
```cpp
while (1)
{
    if(humandetect == 1)
    {
        printf("Detect %d
", eventCounter);
        humandetect = 0;
        while (digitalRead(MOTION))
        {
            printf("high %d
", counter++);
            digitalWrite(BUZZER, 1);
            
            redLedBlink();
            redLedBlink();
            redLedBlink();
            
            takePicture();
            
            redLedBlink();
            redLedBlink();
            redLedBlink();
            
            digitalWrite(BUZZER, 0);
        }
        counter = 0;
    }
    else
    {
        printf("No detect
")
    }
    delay(100);
}
return 0;
}
```

## 개발 결과

1. **시연 사진**:
   - 인체 감지 및 경보 시스템이 작동하는 모습을 보여주는 시연 사진이 포함됩니다.

2. **시연 영상**:
   - 시스템의 작동 모습을 담은 시연 영상을 통해 실제 동작 과정을 확인할 수 있습니다.
   - [시연 영상 보기](https://play-tv.kakao.com/embed/player/cliplink/448363762?service=daum_tistory)

## 참여자

- **권용헌**
- **이윤섭**

## 사용된 기술

- **Raspberry Pi**: 메인 컨트롤러로 사용.
- **Python**: 카메라 제어 및 시스템 로직 구현.
- **C++**: GPIO 제어 및 센서 통신.

## 기대 효과

- **실시간 경보**: 인체의 움직임을 감지하여 실시간으로 경고를 울리고, 현장의 사진을 찍어 기록합니다.
- **활용 가능성**: 금지구역, 군사시설, 기업의 보안 시스템에 활용할 수 있는 효과적인 보안 솔루션을 제공합니다.

## 태그

- Raspberry Pi
- 임베디드 시스템
- 경비 시스템
- 보안 시스템
- 라즈베리 파이 프로젝트
