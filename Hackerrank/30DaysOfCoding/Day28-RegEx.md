# Day 28 : RegEx, Patterns, and Intro to Databases

[문제 상세보기](https://www.hackerrank.com/challenges/30-regex-patterns/problem)

## Flow.

- 정규표현식을 사용해서 **@gmail.com** 을 사용하는 사용자의 FirstName을 **오름차순**으로 정렬해서 출력하는 문제
- 정규표현식 **.*** → 어떤 임의의 문자 0번 이상 발생
- matches : 정규표현식에 만족하는 문자열이면 true
- stream().sorted() : 기본 오름차순 정렬
- .forEach(System.out::println)
    - for(String name : names) {System.out.prinln(name)} 과 동일

## Code.

```java
package hackerrank.days_of_coding;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.ArrayList;
import java.util.List;
import java.util.stream.IntStream;

public class Day28_RegEx {
    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));

        int N = Integer.parseInt(bufferedReader.readLine().trim());
        List<String> names = new ArrayList<>();

        IntStream.range(0, N).forEach(NItr -> {
            try {
                String[] firstMultipleInput = bufferedReader.readLine().split(" ");
                String firstName = firstMultipleInput[0];
                String emailID = firstMultipleInput[1];
                if(emailID.matches( ".*@gmail.com")) {
                    names.add(firstName);
                }
            } catch (IOException ex) {
                throw new RuntimeException(ex);
            }
        });
        names.stream().sorted().forEach(System.out::println);
        bufferedReader.close();
    }
}
```
