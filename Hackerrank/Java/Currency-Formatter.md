# Currency Formatter

[문제 상세보기](https://www.hackerrank.com/challenges/java-currency-formatter/problem)

## Flow.

주어진 Input 을 각국의 통화 형식으로 변환해서 출력하는 문제

- 언어와, 국가로 **Locale** 객체 생성
- NumberFormat 클래스를 사용해서 주어진 Locale 객체를 기반으로 해당 국가 통화 **NumberFormat** 객체 반환 **getCurrencyInstance()**
- format 메서드를 통해 주어진 인풋을 해당 통화 형식으로 출력

### **Locale** 클래스

- 자바에서 지역을 나타내는 클래스
- 특정 지역의 언어, 국가, 지역 설정 정보를 포함

### NumberFormat 클래스

- 자바에서 숫자 형식을 지정하는 클래스

## Code.

```java
import java.text.NumberFormat;
import java.util.Locale;
import java.util.Scanner;

public class Currency_Formatter {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        double payment = scanner.nextDouble();
        scanner.close();

        Locale us = new Locale("en", "US");
        NumberFormat usFormat = NumberFormat.getCurrencyInstance(us);

        Locale india = new Locale("en", "IN");
        NumberFormat indiaFormat = NumberFormat.getCurrencyInstance(india);

        Locale china = new Locale("zh", "CN");
        NumberFormat chinaFormat = NumberFormat.getCurrencyInstance(china);

        Locale france = new Locale("fr", "FR");
        NumberFormat franceFormat = NumberFormat.getCurrencyInstance(france);

        System.out.println("US: " + usFormat.format(payment));
        System.out.println("India: " + indiaFormat.format(payment));
        System.out.println("China: " + chinaFormat.format(payment));
        System.out.println("France: " + franceFormat.format(payment));
    }
}
```
