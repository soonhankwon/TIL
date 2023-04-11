# Static Initializer Block
[문제 상세보기](https://www.hackerrank.com/challenges/java-static-initializer-block/problem)

## Intro.

Static initialization blocks are executed **when the class is loaded**, and you can initialize static variables in those blocks.

- 정적 변수 영역은 JVM의 메모리 영역 중 Runtime Data Area 의 **Method Area**에 위치한다.
- 정적 변수 & 메서드는 **클래스** 수준에서 정의되며, 인스턴스 변수와는 달리 객체에 종속되지 않고 **클래스 자체**에 속한다.
- 따라서, 클래스가 로드될 때 함께 Method Area 에 저장된다.
- **클래스의 수명 주기** 동안 유지
    - 로딩(Class Loader) → 연결 → 초기화 → 사용 (Heap) → 언로딩 (GC)

### Method Area.

- Method Area, Heap Area는 모든 스레드가 **공유**한다.
- **클래스**의 바이트 코드
- **메서드**와 필드의 **이름**
- 데이터 타입 및 상수 풀과 같은 **클래스 수준**의 정보를 저장

JVM이 **클래스를 로드**할 때 사용된다.

- **클래스가 로드**될 때, 해당 클래스의 바이트 코드가 Method Area로 로드
- 일반적으로 PermGen 영역이라고 불렸으나, Java 8 부터 제거
- Java 8 이상의 버전에서는 **Metaspace**라는 용어가 사용된다.

## Flow.

- static 변수 breath, height를 선언하고 초기화 & 사용
- if(b <= 0 || h <= 0) 이면 throw Exception
- else b * h : 면적을 구하는 문제이다.

## Code.

```java
import java.util.Scanner;

public class Static_Initializer_Block {
    static short b;
    static short h;

    public static void main(String[] args) throws Exception {
        Scanner scanner = new Scanner(System.in);
        b = scanner.nextShort();
        h = scanner.nextShort();
        if(b <= 0 || h <= 0) {
            throw new java.lang.Exception("Breadth and height must be positive");
        } else {
            System.out.println(b * h);
        }
    }
}
```
