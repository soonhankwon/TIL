# Date and Time

[문제 상세보기](https://www.hackerrank.com/challenges/java-date-and-time/problem)

## Intro.

자바는 날짜나 요일관련해서 유용한 라이브러리를 제공한다.

- LocalDate 를 사용해서 매개변수 year, month, day 를 변환한다.
    - YYYY-MM-DD
- DayOfWeek 를 사용해서 해당 요일을 구한다.

## Code.

```java
import java.io.*;
import java.time.DayOfWeek;
import java.time.LocalDate;

public class Date_and_Time {
    public static String findDay(int month, int day, int year) {
        LocalDate date = LocalDate.of(year, month, day);
        DayOfWeek dayOfWeek = date.getDayOfWeek();
        return dayOfWeek.toString();
    }

    public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));
        BufferedWriter bufferedWriter = new BufferedWriter(new OutputStreamWriter(System.out));

        String[] firstMultipleInput = bufferedReader.readLine().replaceAll("\\s+$", "").split(" ");

        int month = Integer.parseInt(firstMultipleInput[0]);

        int day = Integer.parseInt(firstMultipleInput[1]);

        int year = Integer.parseInt(firstMultipleInput[2]);

        String res = Date_and_Time.findDay(month, day, year);

        bufferedWriter.write(res);
        bufferedWriter.newLine();

        bufferedReader.close();
        bufferedWriter.close();
    }
}
```
