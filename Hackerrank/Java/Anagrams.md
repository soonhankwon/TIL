# Java Anagrams
[문제 상세보기](https://www.hackerrank.com/challenges/java-anagrams/problem?isFullScreen=true)

## Flow.

- **애너그램**(영어: anagram)은 **단어나 문장을 구성하고 있는 문자의 순서를 바꾸어 다른 단어나 문장을 만드는 것이라고 정의되어 있습니다.**
- 문자의 순서를 바꾸는 것을 생각하면 **순서를 정렬**해주어 비교하면 해당 문자가 애너그램인지 쉽게 판별할 수 있습니다.
- 첫번째로 문자열을 모두 대문자 혹은 소문자로 바꿔줍니다.
    - toUpperCase or toLowerCase
- 애너그램 여부 검사 메서드
    - toCharArray를 사용해서 문자열을 하나 하나 나누어 char[] 배열을 만듭니다.
    - sort 를 사용해 두 배열을 **정렬**합니다.
    - 두 배열이 같은지 검사하여 boolean 으로 리턴합니다.

## Code.

```java
import java.util.Arrays;
import java.util.Scanner;

public class Java_Anagrams {
    static boolean isAnagram(String a, String b) {
        char[] chars = a.toUpperCase().toCharArray();
        char[] chars1 = b.toUpperCase().toCharArray();
        Arrays.sort(chars);
        Arrays.sort(chars1);
        return Arrays.equals(chars, chars1);
    }

    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String a = scan.next();
        String b = scan.next();
        scan.close();
        boolean ret = isAnagram(a, b);
        System.out.println( (ret) ? "Anagrams" : "Not Anagrams" );
    }
}
```
