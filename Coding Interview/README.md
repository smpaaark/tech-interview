# Coding Interview
* [Array](#array)
  * [Two Sum(두 수의 합)](#two-sum두-수의-합)
  * [Remove Duplicates from Sorted Array(정렬된 배열에서 중복 값 제거하기)](#remove-duplicates-from-sorted-array정렬된-배열에서-중복-값-제거하기)
* [LinkedList](#linkedlist)
  * [Merge Two Sorted Lists(정렬된 두 리스트 병합하기)](#merge-two-sorted-lists정렬된-두-리스트-병합하기)
  * [Linked List Cycle(링크드리스트 싸이클)](#linked-list-cycle링크드리스트-싸이클)
* [Stack]()
  * [Valid Parentheses(유효한 괄호)]()
  * [Binary Tree Inorder Traversal(이진 트리 중위 순회)]()
* [참고](#참고)

[목차로](https://github.com/smpark1020/tech-interview#%EB%AA%A9%EC%B0%A8)

## Array
### Two Sum(두 수의 합)
정수 배열 nums와 정수 target이 주어지면 두 수의 합이 target이 되는 값들의 index를 반환합니다.   

정답은 정확히 1개만 존재하며 동일한 요소를 두 번 사용하면 안됩니다.  

정답의 정렬은 어떤 순서이든 상관 없습니다.   

**input**
* 2 <= nums.length <= 104
* -109 <= nums[i] <= 109
* -109 <= target <= 109
* 정답은 무조건 1개 존재합니다.
* 시간복잡도 O(n^2)보다 빠른 복잡도로 풀어야 합니다.

**풀이**  
```
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>(); // Map<값, index> 생성
    for (int i = 0; i < nums.length; i++) {
        if (map.containsKey(target - nums[i])) { // target - nums[i] -> nums[i]가 target이 되기 위해 필요한 값
            return new int[]{i, map.get(target - nums[i])}; // 해당 값이 map에 있으면 현재 index와 target - nums[i]의 index를 리턴
        }

        map.put(nums[i], i); // target - nums[i]이 map에 없으면 현재 값과 index를 map에 추가
    }

    return null;
}
```

[맨위로](#coding-interview)

### Remove Duplicates from Sorted Array(정렬된 배열에서 중복 값 제거하기)
오름차순으로 정렬된 정수 배열이 주어지면 중복된 요소를 제거합니다.   
요소의 순서는 유지되어야 합니다.   

일부 언어에서는 배열 길이를 변경할 수 없으므로 배열의 첫번째 요소부터 결과를 채워서 리턴합니다.   
중복을 제거한 후 k개의 요소가 있는 경우 배열의 첫번째 요소부터 k개 배치해야 합니다.   
배열에 k개의 요소 외에는 어떤 숫자가 있던지 상관 없습니다.   

즉 결과를 첫번째 요소부터 k개의 요소에 넣고 k를 반환합니다.

다른 배열을 생성하면 안됩니다.   
공간 복잡도 O(1)로 문제를 해결해야 합니다.   

다음 코드를 사용하여 정답을 판단합니다.
```
int[] nums = [...]; // Input array
int[] expectedNums = [...]; // The expected answer with correct length

int k = removeDuplicates(nums); // Calls your implementation

assert k == expectedNums.length;
for (int i = 0; i < k; i++) {
    assert nums[i] == expectedNums[i];
}
```

위 코드가 통과한다면 정답입니다.  

**input**
* 0 <= nums.length <= 3 * 104
* -100 <= nums[i] <= 100
* nums는 무작위로 정렬되어 있습니다.

**풀이**
```
public int removeDuplicates(int[] nums) {
    int putIndex  = nums.length > 0 ? 1 : 0; // 중복되지 않는 값이 입력될 index
    for (int num : nums) {
        if (num > nums[putIndex - 1]) { // 입력될 index - 1은 현재까지 중복되지 않은 값 중 마지막 index
            nums[putIndex++] = num; // 중복되지 않은 값이라면 해당 값을 putIndex에 넣고 putIndex를 1 증가시킨다.
        }
    }

    return putIndex; // putIndex가 중복을 제거하고 남은 수들의 갯수이다.
}
```

[맨위로](#coding-interview)

## LinkedList
### Merge Two Sorted Lists(정렬된 두 리스트 병합하기)
정렬된 두 링크드 리스트를 병합한 후 정렬된 리스트를 반환합니다.   
리스트는 처음 두 리스트의 노드들을 합쳐서 만들어야 합니다.   

**input**
* 두 리스트의 노드 갯수는 [0, 50] 범위입니다.
* -100 <= Node.val <= 100
* l1과 l2 모두 오름차순 정렬되어 있습니다.

**풀이**
```
public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    if (l1 == null) { // l1 == null이면 l2 리턴
        return l2;
    }

    if (l2 == null) { // l2 == null이면 l1 리턴
        return l1;
    }

    if(l1.val < l2.val){ // l1보다 l2가 크면 l1.next와 l2 비교
        l1.next = mergeTwoLists(l1.next, l2);
        return l1;
    } else{ // l1이 l2보다 크거나 같으면 l2.next와 l1 비교
        l2.next = mergeTwoLists(l1, l2.next);
        return l2;
    }
}
```

[맨위로](#coding-interview)

### Linked List Cycle(링크드리스트 싸이클)
head가 주어지면 링크드리스트에 cycle이 있는지 확인합니다.   

노드를 계속 따라가다가 이미 순회한 노드가 있을 경우가 cycle이 존재하는 경우입니다.   
내부적으로 pos는 꼬리 노드의 next 노드의 index입니다.   
post는 파라미터로 전달되지 않습니다.   

링크드리스트에 cycle이 있으면 true를 반환합니다.   
없으면 false를 반환합니다.

**input**
* 리스트의 노드 수의 범위는 [0, 104] 입니다.
* -10^5 <= Node.val <= 10^5
* pos는 -1이거나 유요한 index입니다.
* 공간 복잡도 O(1)로 풀어야 합니다.

**풀이**
```
public boolean hasCycle(ListNode head) {
    ListNode slow = head; // 1개씩 이동하는 노드
    ListNode fast = head; // 2개씩 이동하는 노드

    while (fast != null && fast.next != null) { // fast와 fast의 다음노드까지 null이 아닐 경우 순회
        slow = slow.next; // slow 1개 이동
        fast = fast.next.next; // fast 2개 이동

        if (slow == fast) { // slow와 fast가 같은 경우 true 리턴
            return true;
        }
    }

    return false; // while문을 빠져나오면 꼬리가 존재하는 것이므로 false 리턴
}
```

[맨위로](#coding-interview)

## Stack
### Valid Parentheses(유효한 괄호)
'(', ')', '{', '}', '[', ']'로 이루어진 문자열이 주어지면 유효한지 확인합니다.   

유효 조건
1. 여는 괄호는 동일한 유형의 괄호로 닫혀야 합니다.
2. 여는 괄호는 올바른 순서로 닫혀야 합니다.

**input**
* 1 <= s.length <= 104
* s는 괄호 '()[]{}'로만 이루어져 있습니다.

**풀이**
```
public boolean isValid(String s) {
    Stack<Character> stack = new Stack<>(); // 스택 생성
    for (char c : s.toCharArray()) {
        // 여는 괄호일 경우 동일 유형의 닫는 괄호를 stack에 push 한다.
        if (c == '(') {
            stack.push(')');
        } else if (c == '{') {
            stack.push('}');
        } else if (c == '[') {
            stack.push(']');
        } else if (stack.isEmpty() || stack.pop() != c) { // 닫는 괄호일 경우 stack이 비어있거나, 동일한 닫는 괄호가 아닐 경우 false
            return false;
        }
    }

    return stack.isEmpty(); // 여는 괄호만 존재할 경우도 있으므로 stack이 비어있으면 true, 아니면 false이다.
}
```

[맨위로](#coding-interview)

### Binary Tree Inorder Traversal(이진 트리 중위 순회)
이진 트리의 루트가 주어지면 노드의 값을 중위 순회로 반환합니다.   

**input**
* 트리의 노드 수 범위는 [0, 100] 입니다..
* -100 <= Node.val <= 100
* 재귀 말고 반복문으로 해결해야 합니다.

**풀이**
```
public List<Integer> inorderTraversal(TreeNode root) {
    List<Integer> list = new ArrayList<>();

    Stack<TreeNode> stack = new Stack<>();
    TreeNode currentNode = root; // 현재 노드
    while (currentNode != null || !stack.isEmpty()) { // !stack.isEmpty는 오른쪽 노드가 null일 경우 stack에 남아있는 노드로 계속 진행해야 되기 때문에 조건이 있어야 한다.
        while (currentNode != null) { // 왼쪽 노드를 stack에 push 한다.
            stack.push(currentNode);
            currentNode = currentNode.left;
        }

        currentNode = stack.pop();
        list.add(currentNode.val); // stack에서 꺼내서 list에 add
        currentNode = currentNode.right; // 오른쪽 노드로 위 과정 반복
    }

    return list;
}
```

[맨위로](#coding-interview)

## 참고
* [LeetCode](https://leetcode.com/problemset/algorithms/)

[맨위로](#coding-interview)
