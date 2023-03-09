[문제 상세보기](https://www.hackerrank.com/challenges/30-generics/problem?isFullScreen=true)

## Flow.

- Generics 를 사용하여 intArray, stringArray 두 타입을 모두 매개변수로 받는 메서드를 구현하는 문제이다.
- printer 클래스는 제네릭 타입으로 만들어져 있다.
    - 따라서, intPrinter, stringPrinter 인스턴스 생성이 가능하다.
- Integer, String 두 타입의 배열을 받는 메서드 선언
    - public **<T>** void printArray(**T[]** array)

## Code.

```java
package challenges30days;

import java.util.Scanner;

public class Day21_Generics {

	public static void main(String args[]){
        Scanner scanner = new Scanner(System.in);
        int n = scanner.nextInt();
        Integer[] intArray = new Integer[n];
        for (int i = 0; i < n; i++) {
            intArray[i] = scanner.nextInt();
        }

        n = scanner.nextInt();
        String[] stringArray = new String[n];
        for (int i = 0; i < n; i++) {
            stringArray[i] = scanner.next();
        }
        
        Printer<Integer> intPrinter = new Printer<Integer>();
        Printer<String> stringPrinter = new Printer<String>();
        intPrinter.printArray( intArray  );
        stringPrinter.printArray( stringArray );
        if(Printer.class.getDeclaredMethods().length > 1){
            System.out.println("The Printer class should only have 1 method named printArray.");
        }
    } 

}

class Printer <T> {

	public <T> void printArray(T[] array) {
		for(T element : array) {
			System.out.println(element);
		}
	}
}
```
