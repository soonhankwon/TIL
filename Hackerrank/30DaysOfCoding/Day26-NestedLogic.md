# Day 26 : Nested Logic
[문제 상세보기](https://www.hackerrank.com/challenges/30-nested-logic/problem?isFullScreen=true)

## Flow.

- 도서관의 책 반납을 연체했을 경우 연체료를 정산하는 기능

요구사항

- 반납 날짜에 반납했을 경우 fine = 0
- 연체했을 경우 3가지 경우
    - same month and year
        - fine = 15 * number of days late
    - diff month and same year
        - fine = 500 * number of months late
    - diff year
        - fine = 10000
- 자바의 **LocalDate** 클래스의 메서드를 사용
- 예정반납날짜와 실제반납날짜의 차이를 구해서 벌금을 구한다.

## Code.

```java
package challenges30days;
import java.time.LocalDate;
import java.util.Scanner;

public class Day26_NestedLogic {

	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
        String[] returned = scanner.nextLine().split(" ");
        String[] due = scanner.nextLine().split(" ");

        LocalDate dateReturned = LocalDate.of(Integer.parseInt(returned[2]), Integer.parseInt(returned[1]), Integer.parseInt(returned[0]));
        LocalDate dateDue = LocalDate.of(Integer.parseInt(due[2]), Integer.parseInt(due[1]), Integer.parseInt(due[0]));
        Fine fine = new Fine(new Record(dateReturned, dateDue));

        System.out.println(fine.getFine());
    }
}

class Record {
	private LocalDate dateReturned;
	private LocalDate dateDue;
	
	public Record(LocalDate dateReturned, LocalDate dateDue) {
		this.dateReturned = dateReturned;
		this.dateDue = dateDue;
	}
	public LocalDate getDateReturned() {
		return this.dateReturned;
	}
	
	public LocalDate getDateDue() {
		return this.dateDue;
	}
}

class Fine {
	private int fine = 0;
	
	public Fine(Record record) {
		this.fine = calculateFine(record);
	}
	
	private int calculateFine(Record record) {
		if (isDelayed(record)) {
            if (isYearSame(record)) {
                if (isMonthSame(record)) {
                    fine = 15 * (getDaysLate(record));
                } else {
                    fine = 500 * (getMonthsLate(record));
                }
            } else {
                fine = 10000;
            }
        }
		return fine;
	}
	
	private boolean isDelayed(Record record) {
		return record.getDateReturned().isAfter(record.getDateDue());
	}
	
	private boolean isYearSame(Record record) {
		return record.getDateReturned().getYear() == record.getDateDue().getYear();
	}
	
	private boolean isMonthSame(Record record) {
		return record.getDateReturned().getMonth() == record.getDateDue().getMonth();
	}
	
	private int getMonthsLate(Record record) {
		return record.getDateReturned().getMonthValue() - record.getDateDue().getMonthValue();
	}
	
	private int getDaysLate(Record record) {
		return record.getDateReturned().getDayOfMonth() - record.getDateDue().getDayOfMonth();
	}
	
	public int getFine() {
		return this.fine;
	}
}
```
