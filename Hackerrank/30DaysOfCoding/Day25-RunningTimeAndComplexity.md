# Day 25: Running Time and Complexity

[문제 상세보기](https://www.hackerrank.com/challenges/30-running-time-and-complexity/problem?isFullScreen=true)

## Flow.

소수인지 아닌지 판별해서 소수면 Prime, 아니면 Not prime 을 출력하는 문제

- 다만, 만약 가능하다면 O(√n) 의 시간 복잡도로 구현하라고 되어있다.
- 에라스토테네스 채 소수판별 메서드를 사용한다.
    - 2부 터 √n (Math.sqrt) 까지 모든 수로 n을 나눠보는 방식으로 시간복잡도를 구현할 수 있다.
    - 만약 n이 합성수인 경우 n은 a*b 이다.
    - a와 b는 n의 약수이다.
    - a와 b 중 하나는 반드시 √n 이하이다.
    - 따라서, √n 이하의 수로 나눠서 나머지가 0인지 확인하면 n이 소수인지 판별할 수 있다.

### Code.

```java
package challenges30days;

import java.util.Scanner;

public class Day25_RunningTimeAndComplexity {

	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		int t = scanner.nextInt();
		for(int i = 0; i < t; i++) {
			long n = scanner.nextLong();
			if(isPrimeNumber(n)) {
				System.out.println("Prime");
			} else {
				System.out.println("Not prime");
			}
		}
	}
	
	private static boolean isPrimeNumber(long n) {
		if (n <= 1) {
			return false;
		} else if (n == 2) {
			return true;
		}

		for (int i = 2; i <= Math.sqrt(n); i++)
			if (n % i == 0) {
				return false;
			}
		return true;
	}

}
```
