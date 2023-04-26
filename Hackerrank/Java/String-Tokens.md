# String Tokens
[문제 상세보기](https://www.hackerrank.com/challenges/java-string-tokens/problem?isFullScreen=true)

## Flow.

- 문자열을 !,?._' 과 공백 기준으로 스플릿하고 토큰의 갯수와 각 토큰을 프린트하는 알고리즘입니다.
- 정규표현식 [!,?._'@\\s] 을 사용해서 문자열을 나누어 줍니다.
- 특수문자 기준으로 나눈 토큰에 공백 요소가 포함되어 있는 경우가 있습니다.
    - stream filter를 사용해서 공백이 아닌것만 리스트로 컬렉트 해줍니다.
- 컬렉트된 리스트의 크기와 각 요소를 출력해줍니다.

## Code.

```java
import java.util.Arrays;
import java.util.List;
import java.util.Scanner;
import java.util.stream.Collectors;

public class String_Tokens {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String[] tokens = scan.nextLine().split("[!,?._'@\\s]");
        List<String> collect = Arrays.stream(tokens)
                .filter(i -> !i.equals(""))
                        .collect(Collectors.toList());
        System.out.println(collect.size());
        collect.forEach(System.out::println);
        scan.close();
    }
}
```
