# [Java] print, printf, println 차이점
---

## 1. print, println
- `print`: 출력대상을 콘솔에 출력, 줄바꿈 ❌
- `println`: 출력대상을 콘솔에 출력, 줄바꿈 ⭕️

## 2. printf
- `printf`: 자바 1.5 이후부터 도입된 메서드로 서식 지정자를 사용하여 변수의 값을 여러가지 형식으로 변환하여 출력
- 서식 지정자

    |지시자|설명|
    |:---:|:---:|
    |`%b`|boolean 형식으로 출력|
    |`%d`|정수 형식으로 출력|
    |`%o`|8진수 정수의 형식으로 출력|
    |`%x 또는 %X`|16진수 정수의 형식으로 출력|
    |`%f`|소수점 형식으로 출력|
    |`%c`|문자 형식으로 출력|
    |`%s`|문자열 형식으로 출력|
    |`%n`|줄바꿈 기능|
    |`%e 또는 %E`|지수 표현식의 형식으로 출력|

## 3. 사용 예제
- print, println, printf 기본 사용법
    ~~~java
    public class Example {
        public static void main(String[] args) {

            int x = 10;
            int y = 20;
            int a = 123;
            int A = 3;
            char b = 'A';
            String c = "code";

            System.out.print("개행문자 사용하기\n"); // \n 사용

            System.out.println(x + y);
            System.out.println(a + b); // A라는 문자를 아스키코드값 65로 인식
            System.out.println(a + c); // "문자열" + 변수 => 문자열
            System.out.println(b + c); // "문자열" + 문자 => 문자열

            System.out.printf("A = %d %n", A);
            System.out.printf("b = %c %n", b);
            System.out.printf("c = %s %n", c);
        }
    }
    ~~~
    출력 결과
    ```
    개행문자 사용하기
    30
    188
    123code
    Acode
    A = 3 
    b = A 
    c = code 
    ```

- 정수 출력 자리수 지정
    ~~~java
    public class Example {
        public static void main(String[] args) {

            System.out.printf("자리수 미지정 :%d%n",1);
            System.out.printf("자리수 미지정 :%d%n",10);
            System.out.printf("자리수 미지정 :%d%n",100);
            System.out.printf("자리수 미지정 :%d%n%n",1000);
            
            //자리수 지정했을 경우 오른쪽으로 정렬 (남는 자리수는 공백)
            System.out.printf("자리수 지정 :%4d%n",1);
            System.out.printf("자리수 지정 :%4d%n",10);
            System.out.printf("자리수 지정 :%4d%n",100);
            System.out.printf("자리수 지정 :%4d%n%n",1000);
            
            //자리수 지정 후 '0'사용하면 오른쪽으로 정렬된다 (왼쪽 자리수는 0으로 채움)
            System.out.printf("자리수 지정('0'사용) :%04d%n",1);
            System.out.printf("자리수 지정('0'사용) :%04d%n",10);
            System.out.printf("자리수 지정('0'사용) :%04d%n",100);
            System.out.printf("자리수 지정('0'사용) :%04d%n%n",1000);

        }
    }
    ~~~
    출력 결과
    ```
    자리수 미지정 :1
    자리수 미지정 :10
    자리수 미지정 :100
    자리수 미지정 :1000

    자리수 지정 :   1
    자리수 지정 :  10
    자리수 지정 : 100
    자리수 지정 :1000

    자리수 지정('0'사용) :0001
    자리수 지정('0'사용) :0010
    자리수 지정('0'사용) :0100
    자리수 지정('0'사용) :1000
    ```

- 소수점 자리수
    ~~~java
    public class Example {
        public static void main(String[] args) {

            int num1 = 1;
            double num2 = 12.3456;

            System.out.printf("num1: %d %n",num1);
            System.out.printf("num2: %f %n",num2);
            System.out.printf("num2(소수점 첫째 자리까지): %.1f%n", num2);
            System.out.printf("num2(소수점 둘째 자리까지): %.2f%n", num2);
            System.out.printf("num2(소수점 셋째 자리까지): %.3f%n", num2);

        }
    }
    ~~~
    출력 결과
    ```
    num1: 1 
    num2: 12.345600 
    num2(소수점 첫째 자리까지): 12.3
    num2(소수점 둘째 자리까지): 12.35
    num2(소수점 셋째 자리까지): 12.346
    ```