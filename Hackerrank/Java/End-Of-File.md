# End-of-file
[문제 상세보기](https://www.hackerrank.com/challenges/java-end-of-file/problem)

## Intro.

**EOF(End of file)** 은 데이터 소스로부터 더 이상 읽을 수 있는 데이터가 없음을 의미한다.

- Scanner 와 BufferedReader 의 EOF 처리
- **BufferedReader** 가 성능면에서 우월하다.

## Code1.

```java
import java.io.*;

public class End_Of_File {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        String input;
        int index = 1;
        while((input = br.readLine()) != null) {
            System.out.println(index + " " + input);
            index++;
        }
    }
}
```

## Code2.

```java
import java.io.*;
import java.util.Scanner;

public class End_Of_File {
    public static void main(String[] args) throws IOException {
        Scanner scanner = new Scanner(System.in);
        int index = 1;
        while(scanner.hasNextLine()) {
            System.out.println(index + " " + scanner.nextLine());
            index++;
        }
    }
}
```
