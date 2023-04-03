# Day 27 : Testing

[문제 상세보기](https://www.hackerrank.com/challenges/30-testing/problem?isFullScreen=true)

## Flow.

---

- 동료의 단위 테스트 코드를 위해 Mock 정적 클래스를 구현하는 문제이다.
- 정적 클래스의 메서드를 호출할 때 기대되는 값이 나오도록 그대로 구현하면 된다.
- 실제로 단위 테스트를 만들때, Mockito를 사용해서 기대하는 값을 주도록 설정해서 사용하고 있다.

## Code.

---

```java
import java.util.*;

public class Solution {

    public static int minimum_index(int[] seq) {
        if (seq.length == 0) {
            throw new IllegalArgumentException("Cannot get the minimum value index from an empty sequence");
        }
        int min_idx = 0;
        for (int i = 1; i < seq.length; ++i) {
            if (seq[i] < seq[min_idx]) {
                min_idx = i;
            }
        }
        return min_idx;
    }
    
static class TestDataEmptyArray {
    public static int[] get_array() {
        return new int[0];
    }
}

static class TestDataUniqueValues {
    static int[] get_array() {
        return new int[]{1, 2, 3};
    }

    static int get_expected_result() {
        return 0;
    }
}

static class TestDataExactlyTwoDifferentMinimums {
    static int[] get_array() {
        return new int[]{1, 1, 2};
    }
    static int get_expected_result() {
        return 0;
    }
}
    
	public static void TestWithEmptyArray() {
        try {
            int[] seq = TestDataEmptyArray.get_array();
            int result = minimum_index(seq);
        } catch (IllegalArgumentException e) {
            return;
        }
        throw new AssertionError("Exception wasn't thrown as expected");
    }

    public static void TestWithUniqueValues() {
        int[] seq = TestDataUniqueValues.get_array();
        if (seq.length < 2) {
            throw new AssertionError("less than 2 elements in the array");
        }

        Integer[] tmp = new Integer[seq.length];
        for (int i = 0; i < seq.length; ++i) {
            tmp[i] = Integer.valueOf(seq[i]);
        }
        if (!((new LinkedHashSet<Integer>(Arrays.asList(tmp))).size() == seq.length)) {
            throw new AssertionError("not all values are unique");
        }

        int expected_result = TestDataUniqueValues.get_expected_result();
        int result = minimum_index(seq);
        if (result != expected_result) {
            throw new AssertionError("result is different than the expected result");
        }
    }

    public static void TestWithExactlyTwoDifferentMinimums() {
        int[] seq = TestDataExactlyTwoDifferentMinimums.get_array();
        if (seq.length < 2) {
            throw new AssertionError("less than 2 elements in the array");
        }

        int[] tmp = seq.clone();
        Arrays.sort(tmp);
        if (!(tmp[0] == tmp[1] && (tmp.length == 2 || tmp[1] < tmp[2]))) {
            throw new AssertionError("there are not exactly two minimums in the array");
        }

        int expected_result = TestDataExactlyTwoDifferentMinimums.get_expected_result();
        int result = minimum_index(seq);
        if (result != expected_result) {
            throw new AssertionError("result is different than the expected result");
        }
    }

    public static void main(String[] args) {
        TestWithEmptyArray();
        TestWithUniqueValues();
        TestWithExactlyTwoDifferentMinimums();
        System.out.println("OK");
    }
}
```
