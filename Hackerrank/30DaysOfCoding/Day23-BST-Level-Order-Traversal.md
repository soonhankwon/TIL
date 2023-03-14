# Day 23: BST Level-Order Traversal

[문제 상세보기](https://www.hackerrank.com/challenges/30-binary-trees/problem?isFullScreen=true)

### Level-Order Traveral

트리의 레벨 순서대로 순회하는 방법

- 루트 노드를 방문한다.
- 루트 노드의 Left Child 를 방문한다.
- 루트 노드의 Right Child 를 방문한다.
- BFS 랑 같은 방식

### Flow.

- BFS 랑 같은 방식임으로 Queue를 통해서 구현한다.
    
    ![https://github.com/ChanhuiSeok/chanhuiseok.github.io/blob/master/assets/img/sample/ds_4.png?raw=true](https://github.com/ChanhuiSeok/chanhuiseok.github.io/blob/master/assets/img/sample/ds_4.png?raw=true)
    
- 맨 먼저 큐에 루트 노드를 넣는다.
    - 큐 : 1
- Dequeue 연산으로 ptr에 반환한다. (ptr = pointer)
    - 큐 : empty
    - ptr : 1
- 반환한 ptr의 데이터를 출력하고, dequeue했던 1의 left, right Child를 큐에 넣는다.
    - 큐 : 2, 3
    - 출력 : 1
- Dequeue 연산으로 ptr에 반환한다.
    - 큐 : 3
    - ptr : 2
- 반환한 ptr의 데이터를 출력하고, dequeue했던 2의 left, right Child를 큐에 넣는다.
    - 큐 : 3, 4, 5
    - 출력 : 1, 2
- Dequeue 연산으로 ptr에 반환한다.
    - 큐 : 4, 5
    - ptr : 3
- 반환한 ptr의 데이터를 출력하고, dequeue했던 3의 left, right Child를 큐에 넣어야 하지만 child node가 없음으로 넣을것이 없다.
    - 큐 : 4, 5
    - 출력 : 1, 2, 3
- Dequeue 연산으로 ptr에 반환한다.
    - 큐 : 5
    - ptr : 4
- 반환한 ptr의 데이터를 출력하고, dequeue했던 4의 left, right Child를 큐에 넣어야 하지만 child node가 없음으로 넣을것이 없다.
    - 큐 : 5
    - 출력 : 1, 2, 3, 4
- Dequeue 연산으로 ptr에 반환한다.
    - 큐 : empty
    - ptr : 5
- 반환한 ptr의 데이터를 출력, 큐에는 아무것도 없음으로 순회 끝
    - 출력 : 1, 2, 3, 4, 5

### Code.

```java
import java.util.*;
import java.io.*;

class Node {
	Node left, right;
	int data;

	Node(int data) {
		this.data = data;
		left = right = null;
	}
}

class Solution {

	static void levelOrder(Node root) {
		Queue<Node> q = new LinkedList<>();
		q.add(root);

		while (!q.isEmpty()) {
			Node nowNode = q.poll();
			if (nowNode.left != null && nowNode.right == null) {
				q.add(nowNode.left);
			}
			if (nowNode.left == null && nowNode.right != null) {
				q.add(nowNode.right);
			}
			if (nowNode.left != null && nowNode.right != null) {
				q.add(nowNode.left);
				q.add(nowNode.right);
			}
			System.out.print(nowNode.data + " ");
		}

	}

	public static Node insert(Node root, int data) {
		if (root == null) {
			return new Node(data);
		} else {
			Node cur;
			if (data <= root.data) {
				cur = insert(root.left, data);
				root.left = cur;
			} else {
				cur = insert(root.right, data);
				root.right = cur;
			}
			return root;
		}
	}

	public static void main(String args[]) {
		Scanner sc = new Scanner(System.in);
		int T = sc.nextInt();
		Node root = null;
		while (T-- > 0) {
			int data = sc.nextInt();
			root = insert(root, data);
		}
		levelOrder(root);
	}
}
```
