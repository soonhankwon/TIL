# Substring Comparisons
[문제 상세보기](https://www.hackerrank.com/challenges/java-string-compare/problem?isFullScreen=true)

## Flow.

- Input 문자열 s
- 주어진 k자리수 문자열 → 슬라이딩 윈도우
    - substring(startIndex, k)
- 슬라이딩 윈도우를 움직이며 사전순으로 비교한다.
    - String.compareTo()
    - compareTo() > 0 사전순으로 뒤에오는 경우
    - compareTo() < 0 사전순으로 앞에오는 경우

## Code.

```java
import java.util.Scanner;

public class Substring_Comparisons {

    public static String getSmallestAndLargest(String s, int k) {
        String smallest = "";
        String largest = "";

        int startIndex = 0;
        int endIndex = k;
        while (endIndex != s.length() + 1) {
            String slidingWindow = s.substring(startIndex, endIndex);
            if (smallest.length() == 0) {
                smallest = slidingWindow;
                largest = slidingWindow;
            }
            if (slidingWindow.compareTo(smallest) < 0) {
                smallest = slidingWindow;
            }
            if (slidingWindow.compareTo(largest) > 0) {
                largest = slidingWindow;
            }
            startIndex++;
            endIndex++;
        }

        return smallest + "\n" + largest;
    }

    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);
        String s = scan.next();
        int k = scan.nextInt();
        scan.close();

        System.out.println(getSmallestAndLargest(s, k));
    }
}
```
