# Arduino2021


### 서종완교수님의 메이커스워크샵 수업에 기반한 내용입니다.

##### 0311
```
<아두이노의 기본 구조>

setup()
- 전원을 공급한 직후/reset스위치를 누른 직후
 1회만 실행

loop()
- 무한반복 실행
 기록한 순서대로... 

setup(),loop() 두개의 블록으로 구성

-------------------------------------------------
<프로그래밍 개념>
순차-기록한 순서대로 하나씩 실행
반복-지정한 구간/횟수/조건에 따라 순차동작을 반복함
조건- 지정된 순간에 특정한 동작을 발생
함수-순차, 반복, 조건을 포함한 동작 단위를 
      하나의 이름으로 묶어 다음에 사용할 때
      활용성을 높이는 제어블록

--------------------------------------------------
*대/소문자 구분해야함.

pinMode(핀번호, 입/출력 상태)
  pinMode(5,OUTPUT);

핀번호:0~13,A0~A5
입/출력상태: INPUT,OUTPUT
	  INPUT_PULLUP(나중에 설명해주심)

digitalWrite(핀번호,출력값)
출력값:HIGH(전원공급함),LOW(전원공급 안함)

delay(값)
 (1/1000 *값)초를 delay

진짜 시간 이용해야할때 rtc(real time clock?) 사용


ex
목적: 자동온도/습도 제어장치
기능: 일정한온도/습도범위로 실내온도/습도 유지
방법?22-24도 유지하고싶다  40%-60%
 실내 온도 측정          습도
 온도 <22 : 난방 켜기    제습
 온도 >24 : 냉방 켜기    가습
 
동작순서
온도 저장 변수:temperature
 온도측정
  측정된 온도에 따라 동작
   온도<22: 난방 켜기, 냉방 끄기
   22<=온도<=24:모두 끄기
   24<온도: 냉방 켜기, 난방 끄기
냉방장치 연결핀:10
난방장치 연결핀:8

```

##### 0318
```
float f; //double float는 아두이노에서는 4바이트
f=3.14;
10진수에서 소수점이있는 값을 컴퓨터에서 2진수로 처리할 때
숫자 변환 원리상 정확한 2진수로 변환이 불가능함.
따라서 소수점이 있는 숫자는 항상 오차가 있음.
1/2,1/4,1/8...

float로 선언된 변수와 숫자를 비교할 때는 
절대 같다(==),같지않다(!=)를 사용하면 안됨. 
대신 같거나 크다, 같거나 작다, 작다,크다와 같은 연산은 가능


char a; 문자저장 8bit
//java char:2byte

short int(2-Byte)
signed short int->short   -32765~+32768
unsigned short int -> unsigned short    0~65535

long int(4-Byte)
signed long int  -21억~+21억
unsigned long int 0~42억

int i; i가 가지는 메모리 크기는?
16 bit 이하의 컴퓨터에서는 short int,
32 bit 이상의 컴퓨터에서는 long int로 동작

기본 arduino uno는 16bit ->2byte

short int 약 -30000~30000
long int 약 -21억~21억

pinMode(pin번호, 입/출력모드);
pin번호:0-13,A0-A5(가급적 0과 1은 PC와 통신에 사용하므로
안쓰는 것이 좋음)

입/출력모드: INPUT,OUTPUT
	INPUT_PULLUP

digitalWrite(pin번호, 값)

값: HIGH,LOW
변수=digitalRead(pin번호);
pin번호의 현재상태를 읽어 변수에 저장
변수에 저장되는 값은 HIGH 또는 LOW

푸쉬버튼: 버튼을 누르면 단자 연결. 떼면 단자 연결x

gnd가 연결이 안됐으면 들어오는 값의 신호가 LOW인지 HIGH인지
잘 구분이 안됨 -> 그래서 LOW라고 알려주려고 gnd에 연결
```

#### 내용이 많아 0325부터는 txt file로 올림
