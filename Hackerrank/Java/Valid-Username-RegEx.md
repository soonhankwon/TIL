# Valid Username Regular Expression
[문제 상세보기](https://www.hackerrank.com/challenges/valid-username-checker/problem?isFullScreen=true)

## Flow.

- **정규표현식**을 사용한 이름 유효성 검사 알고리즘
- String regularExpression = "^[a-zA-Z]\\w{7,29}$"
    - ^ : 문자열의 시작
    - [a-zA-Z] : a 부터 Z
    - \w : **알파벳 대소문자, 숫자 및 밑줄과 일치**하는 문자 중 하나
    - {7,29} : 전체 문자열의 길이는 8 에서 30 사이
    - $ : 문자열의 끝

## Code.

```java
import java.util.Scanner;

class UsernameValidator {
    static final String regularExpression = "^[a-zA-Z]\\w{7,29}$";
}

public class Valid_Username_Regular_Expression {
    private static final Scanner scan = new Scanner(System.in);

    public static void main(String[] args) {
        int n = Integer.parseInt(scan.nextLine());
        while (n-- != 0) {
            String userName = scan.nextLine();

            if (userName.matches(UsernameValidator.regularExpression)) {
                System.out.println("Valid");
            } else {
                System.out.println("Invalid");
            }
        }
    }
}
```
