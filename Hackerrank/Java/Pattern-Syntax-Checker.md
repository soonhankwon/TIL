# Pattern Syntax Checker
[문제 상세보기](https://www.hackerrank.com/challenges/pattern-syntax-checker/problem?isFullScreen=true)

## Flow.

- 정규표현식이 맞는 표현식인가 검증하는 알고리즘 입니다.
- 주어진 **정규표현식으로 패턴을 만드는 compile(String regex)** 메서드를 사용하여 구현했습니다.
- 주어진 정규표현식을 패턴으로 만들수 없다면 PatternSyntaxException (Checked Exception) 이 발생합니다.
- 패턴으로 만들 수 있다면 Valid, 아니라면 익셉션을 캐치해 Invalid를 출력합니다.

## Code.

```java
import java.util.Scanner;
import java.util.regex.Pattern;
import java.util.regex.PatternSyntaxException;

public class Pattern_Syntax_Checker {
    public static void main (String[]args){
        Scanner in = new Scanner(System.in);
        int testCases = Integer.parseInt(in.nextLine());
        while (testCases > 0) {
            String pattern = in.nextLine();
            try {
                Pattern.compile(pattern);
                System.out.println("Valid");
            } catch (PatternSyntaxException e) {
                System.out.println("Invalid");
            }
            testCases--;
        }
    }
}
```
