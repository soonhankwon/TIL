# Day 24: More Linked Lists

[문제 상세보기](https://www.hackerrank.com/challenges/30-linked-list-deletion/problem?isFullScreen=true)

## List Collection

리스트 자료구조는 중복 저장을 허용하며 데이터를 나란히 저장한다.

자바에는 리스트 자료구조를 정의해놓은 List 컬렉션이 있다. (인터페이스)

- 객체를 **인덱스**로 관리하여 객체를 삽입하면 인덱스가 자동으로 부여된다.
- 인덱스로 검색, 삭제가 가능하다.
- 객체를 직접 저장하고 있지 않고 객체의 주소를 가지고 있다.
- 구현체로는 ArrayList, LinkedList, Vector 등이 있다.

### Linked List

List 인터페이스의 구현체로 **메모리의 동적할당**을 기반으로 구현된 리스트

LinkedList의 모든 노드는 인접 노드를 참조해서 체인처럼 관리한다.

![https://t1.daumcdn.net/cfile/tistory/99CEE2425CB7F7CB10](https://t1.daumcdn.net/cfile/tistory/99CEE2425CB7F7CB10)

노드를 리스트의 중간에 삽입하여도 인접한 노드들의 링크만 변경하면 되고, 다른 노드에는 영향이 없다.

- 따라서, 빈번한 삽입, 삭제가 일어날 때 적합하다.

### Flow.

- 문제는 LinkedList에서 중복을 제거하는 메서드를 구현하는 것이다.
- 중복을 허용하지않는 HashSet을 사용해서 다음 노드의 데이터가 Set에 있으면 pointer(next) 가 다음 다음 노드를 가리키게 바꿔준다.
- Set에 다음 노드의 데이터가 없다면, pointer가 다음 노드를 가리키게 한다.

### Code.

```java
import java.io.*;
import java.util.*;

class Node {
	int data;
	Node next;

	Node(int d) {
		data = d;
		next = null;
	}

}

class Solution {

	public static Node removeDuplicates(Node head) {
		Set<Integer> set = new HashSet<>();
		Node currentNode = head;
		set.add(currentNode.data);
		while (currentNode != null && currentNode.next != null) {
			if (set.contains(currentNode.next.data)) {
				currentNode.next = currentNode.next.next;
			} else {
				currentNode = currentNode.next;
				set.add(currentNode.data);
			}
		}
		return head;

	}

	public static Node insert(Node head, int data) {
		Node p = new Node(data);
		if (head == null)
			head = p;
		else if (head.next == null)
			head.next = p;
		else {
			Node start = head;
			while (start.next != null)
				start = start.next;
			start.next = p;

		}
		return head;
	}

	public static void display(Node head) {
		Node start = head;
		while (start != null) {
			System.out.print(start.data + " ");
			start = start.next;
		}
	}

	public static void main(String args[]) {
		Scanner sc = new Scanner(System.in);
		Node head = null;
		int T = sc.nextInt();
		while (T-- > 0) {
			int ele = sc.nextInt();
			head = insert(head, ele);
		}
		head = removeDuplicates(head);
		display(head);

	}
}
```
