[문제 상세보기](https://www.hackerrank.com/challenges/30-sorting/problem?isFullScreen=true)

## Summary.

- 버블 소트를 구현하는 문제
- 버블 소트란?
    - 정렬 성능이 최악인 녀석, 하지만 간단하다.
    - 인접한 두 요소를 비교하여 순서가 잘못된 경우 서로 위치를 바꾼다.
    - 리스트가 완전히 정렬될 때 까지 반복
    - 모든 요소를 비교하기 때문에 최악의 경우 **시간복잡도 : O(n^2)**

## Code.

```java
package challenges30days;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class Day20_Sorting {

	public static void main(String[] args) throws IOException {
        BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(System.in));

        int n = Integer.parseInt(bufferedReader.readLine().trim());

        List<Integer> a = Stream.of(bufferedReader.readLine().replaceAll("\\s+$", "").split(" "))
            .map(Integer::parseInt)
            .collect(Collectors.toList());
        
        int numberOfSwaps = 0;
        for(int i = 0; i < n; i++) {	
        	for(int j = 0; j < n-1; j++) {
        		if(a.get(j) > a.get(j+1)) {
        			int temp = a.get(j+1);
        			a.set(j+1, a.get(j));
        			a.set(j, temp);
        			numberOfSwaps++;
        		}
        	}
        	if (numberOfSwaps == 0) {
                break;
            }
        }
        
        System.out.println("Array is sorted in " + numberOfSwaps + " swaps.");
        System.out.println("First Element: " + a.get(0));
        System.out.println("Last Element: " + a.get(n-1));

        bufferedReader.close();
    }

}
```
