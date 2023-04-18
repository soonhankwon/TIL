# Substring

[문제 상세보기](https://www.hackerrank.com/challenges/java-substring/problem?isFullScreen=true)

## Intro.

- String substring(int index)
- String substring(int beginIndex, int endIndex)

```java
String str = "코딩배우기";
Assertions.assertThat(str.substring(2)).isEqualTo("배우기");
Assertions.assertThat(str.substring(1,2).isEqualTo("딩");

```

## Code.

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

public class Solution {

    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        String S = in.next();
        int start = in.nextInt();
        int end = in.nextInt();
        
        System.out.println(S.substring(start,end));
    }
}
```
