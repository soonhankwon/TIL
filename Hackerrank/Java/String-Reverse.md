# String Reverse
[문제 상세보기](https://www.hackerrank.com/challenges/java-string-reverse/problem?isFullScreen=true)

## Flow.

- 펠린드롬 알고리즘 (앞으로 읽어도, 거꾸로 읽어도 같은 문자열) 이다.
- StringBuilder 를 사용해서 문자열을 reverse().toString()
- 뒤집은 문자열을 Input 문자열과 비교해서 출력

## Code.

```java
import java.util.Scanner;

public class String_Reverse {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String A = sc.next();
        sc.close();

        System.out.println(A.equals(new StringBuilder(A)
                .reverse()
                .toString()) ? "Yes" : "No");
    }
}
```
