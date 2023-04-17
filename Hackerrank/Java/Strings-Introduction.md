# Strings Introduction
[문제 상세보기](https://www.hackerrank.com/challenges/java-strings-introduction/problem?isFullScreen=true)

## Flow.

- String A, B의 문자열 길이의 합
    - **length()**
- A is lexicographically greater than otherwise print **No**
    - 사전식으로 A 가 B 보다 먼저 나온다면 print No
    - **charAt()** 으로 비교
- 문자열의 앞글자를 **대문자**로 바꿔서 출력
    - **substring()** & **toUppercase()**

## Code.

```java
import java.util.Scanner;

public class Strings_Introduction {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String A = sc.next();
        String B = sc.next();

        System.out.println(A.length() + B.length());
        if (A.charAt(0) <= B.charAt(0)) {
            System.out.println("No");
        } else {
            System.out.println("Yes");
        }
        A = A.substring(0, 1).toUpperCase() + A.substring(1);
        B = B.substring(0, 1).toUpperCase() + B.substring(1);

        System.out.println(A + " " + B);
    }
}
```
