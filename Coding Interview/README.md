# Coding Interview
* [Array](#array)
  * [Two Sum(두 수의 합)](#two-sum두-수의-합)
  * [Remove Duplicates from Sorted Array(정렬된 배열에서 중복 값 제거하기)](#remove-duplicates-from-sorted-array정렬된-배열에서-중복-값-제거하기)
* [LinkedList](#linkedlist)
  * [Merge Two Sorted Lists(정렬된 두 리스트 병합하기)](#merge-two-sorted-lists정렬된-두-리스트-병합하기)
  * [Linked List Cycle(링크드리스트 싸이클)](#linked-list-cycle링크드리스트-싸이클)
* [Stack](#stack)
  * [Valid Parentheses(유효한 괄호)](#valid-parentheses유효한-괄호)
  * [Binary Tree Inorder Traversal(이진 트리 중위 순회)](#binary-tree-inorder-traversal이진-트리-중위-순회)
* [Queue](#queue)
  * [First Unique Character in a String(문자열의 첫 고유한 문자)](#first-unique-character-in-a-string문자열의-첫-고유한-문자)
  * [Flatten Nested List Iterator(중첩된 리스트 Flatten(평탄화))](#flatten-nested-list-iterator중첩된-리스트-flatten평탄화)
* [Tree](#tree)
  * [Symmetric Tree(대칭 트리)](#symmetric-tree대칭-트리)
  * [Maximum Depth of Binary Tree(이진 트리의 최대 깊이)](#maximum-depth-of-binary-tree이진-트리의-최대-깊이)
* [Heap](#heap)
  * [Kth Largest Element in an Array(배열에서 k번째로 큰 요소)](#kth-largest-element-in-an-array배열에서-k번째로-큰-요소)
  * [Top K Frequent Elements(빈도 높은 요소 Top K)](#top-k-frequent-elements빈도-높은-요소-top-k)
* [Graph](#graph)
  * [Course Schedule(강의 일정)](#course-schedule강의-일정)
  * [Course Schedule II(강의 일정 2)](#course-schedule-ii강의-일정-2)
* [HashTable](#hashtable)
  * [Roman to Integer(로마 숫자를 정수로 변환)](#roman-to-integer로마-숫자를-정수로-변환)
  * [Linked List Cycle(링크드리스트 싸이클)](#linked-list-cycle링크드리스트-싸이클-1)
* [recursion](#recursion)
  * [Reverse Linked List(링크드 리스트 뒤집기)](#reverse-linked-list링크드-리스트-뒤집기)
  * [Palindrome Linked List(회문 링크드 리스트)](#palindrome-linked-list회문-링크드-리스트)
* [Backtracking](#backtracking)
  * [Letter Combinations of a Phone Number(전화번호의 문자 조합)](#letter-combinations-of-a-phone-number전화번호의-문자-조합)
  * [Generate Parentheses(괄호 생성)](#generate-parentheses괄호-생성)
* [Dynamic Programming](#dynamic-programming)
  * [Maximum Subarray(부분배열 합의 최대값)](#maximum-subarray부분배열-합의-최대값)
  * [Climbing Stairs(계단 오르기)](#climbing-stairs계단-오르기)
* [Sorting](#sorting)
  * [Merge Sorted Array(배열의 병합 정렬)](#merge-sorted-array배열의-병합-정렬)
  * [Majority Element(과반수 요소)](#majority-element과반수-요소)
* [Binary Search](#binary-search)
  * [Sqrt(x)(제곱근 x)](#sqrtx제곱근-x)
  * [Intersection of Two Arrays II(두 배열의 교집합 2)](#intersection-of-two-arrays-ii두-배열의-교집합-2)
* [DFS](#dfs)
  * [Binary Tree Inorder Traversal(이진 트리 중위 순회)](#binary-tree-inorder-traversal이진-트리-중위-순회-1)
  * [Symmetric Tree(대칭 트리)](#symmetric-tree대칭-트리-1)
* [BFS](#bfs)
  * [Symmetric Tree(대칭 트리)](#symmetric-tree대칭-트리-2)
  * [Maximum Depth of Binary Tree(이진 트리의 최대 깊이)](#maximum-depth-of-binary-tree이진-트리의-최대-깊이-1)
* [Bit Manipulation](#bit-manipulation)
  * [Single Number(1개만 존재하는 수 찾기)](#single-number1개만-존재하는-수-찾기)
  * [Reverse Bits(비트 뒤집기)](#reverse-bits비트-뒤집기)
* [String](#string)
  * [Longest Common Prefix(가장 긴 공통 접두사)](#longest-common-prefix가장-긴-공통-접두사)
  * [Implement strStr()(strStr() 구현)](#implement-strstrstrstr-구현)
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

**example**
```
Input: l1 = [1,2,4], l2 = [1,3,4]
Output: [1,1,2,3,4,4]
```

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

**example**
```
Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
```

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

**example**
```
Input: root = [1,null,2,3]
Output: [1,3,2]
```

**풀이**
```
public List<Integer> inorderTraversal(TreeNode root) {
    List<Integer> list = new ArrayList<>();

    Stack<TreeNode> stack = new Stack<>();
    TreeNode currentNode = root; // 현재 노드
    while (currentNode != null || !stack.isEmpty()) { // !stack.isEmpty는 오른쪽 노드가 null일 경우 stack에 남아있는 노드로 계속 진행해야 되기 때문에 조건이 있어야 한다.
        while (currentNode != null) { // 현재 노드를 stack에 push하고 왼쪽노드로 바꾼다. -> 이것을 왼쪽 끝 노드까지 반복
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

## Queue
### First Unique Character in a String(문자열의 첫 고유한 문자)
문자열이 주어지면 반복되지 않는 첫번째 문자를 찾고 index를 반환합니다.   
없으면 -1을 반환합니다.   

**input**
* 1 <= s.length <= 105
* s는 영어 소문자로만 구성됩니다.   

**풀이**
```
public int firstUniqChar(String s) {
    Map<Character,Integer> map = new HashMap<>();
    Queue<Integer> queue = new LinkedList<>();
    
    for(int i = 0; i < s.length(); i++){
        char c = s.charAt(i);
        if(!map.containsKey(c)){ // map에 없으면 queue에 해당 index를 넣고 map에도 추가한다.
            queue.offer(i);
            map.put(c, 1);
        } else{ // map에 있으면 map의 값을 +1 증가시킨다.
            map.put(c, map.get(c) + 1);
        }

        while(!queue.isEmpty() && map.get(s.charAt(queue.peek())) > 1) { // queue의 맨 앞 값으로 map을 조회해서 1보다 크면 해당 인덱스를 queue에서 제거한다.
            queue.poll();
        }
    }

    if(queue.isEmpty()) { // queue가 비어있으면 -1 리턴
        return -1;
    }

    return queue.peek(); // queue의 맨 앞 index 리턴
}
```

배열로도 풀 수 있습니다.
```
public int firstUniqChar(String s) {
    int[] alphabet = new int[26];
    for (char c : s.toCharArray()) {
        alphabet[c - 'a']++;
    }

    for (int i = 0; i <s.length(); i++) {
        if (alphabet[s.charAt(i) - 'a'] == 1) {
            return i;
        }
    }

    return -1;
}
```

[맨위로](#coding-interview)

### Flatten Nested List Iterator(중첩된 리스트 Flatten(평탄화))
중첩된 정수 리스트가 주어집니다.   
각 요소는 정수 또는 리스트이며 리스트의 요소도 정수 또는 리스트일 수 있습니다.   
반복문을 사용하여 flatten(평탄화) 합니다.

NestedIterator 클래스를 구현합니다.
* NestedIterator(List\<NestedInteger> nestedList)
  * 초기화 합니다.
* int next()
  * 중첩 리스트의 다음 정수를 반환합니다.   
* boolean hasNext()
  * 중첩 리스트에 정수가 남아 있으면 true를 반환하고 그렇지 않으면 false를 반환합니다.

다음 의사코드를 사용하여 코드를 테스트합니다.
```
initialize iterator with nestedList
res = []
while iterator.hasNext()
    append iterator.next() to the end of res
return res
```

res가 예상된 결과와 일치하면 코드가 올바른 것으로 판단됩니다.   

**input**
* 1 <= nestedList.length <= 500
* 중첩 리스트의 정수 값은 [-106, 106] 범위에 있습니다.

**Example**
```
Input: nestedList = [[1,1],2,[1,1]]
Output: [1,1,2,1,1]
Explanation: By calling next repeatedly until hasNext returns false, the order of elements returned by next should be: [1,1,2,1,1].
```

**풀이**   
Deque를 사용한 풀이
```
class NestedIterator implements Iterator<Integer> {

    Deque<NestedInteger> deque = new ArrayDeque<>();

    public NestedIterator2(List<NestedInteger> nestedList) {
        prepareStack(nestedList);
    }

    @Override
    public Integer next() {
        if (!hasNext()) { // deque가 비어있으면 null
            return null;
        }
        return deque.pop().getInteger(); // 이때 deque의 맨 앞 값은 항상 정수이다.
    }

    @Override
    public boolean hasNext() { // deque의 맨 앞 요소를 정수로 만들어주는 작업을 한다.
        while (!deque.isEmpty() && !deque.peek().isInteger()) { // deque의 맨 앞 요소가 정수가 아니면 반복
            List<NestedInteger> list = deque.pop().getList(); // deque의 맨 앞 리스트를 꺼냅니다.
            prepareStack(list); // prepareStack 호출하여 리스트의 요소들을 하나하나 deque의 앞쪽에 쌓는다.
        }
        return !deque.isEmpty();
    }

    private void prepareStack(List<NestedInteger> nestedList) {
        for (int i = nestedList.size() - 1; i >= 0; i--) { // 마지막 요소부터 push하여 첫 요소가 deque의 맨 앞에 오게 합니다.
            deque.push(nestedList.get(i));
        }
    }

}
```

Queue를 사용하는 풀이
```
class NestedIterator implements Iterator<Integer> {

    private Queue<Integer> queue = new LinkedList<>();

    public NestedIterator(List<NestedInteger> nestedList) {
        initQueue(nestedList);
    }

    private void initQueue(List<NestedInteger> nestedList) {
        for (NestedInteger nestedInteger : nestedList) {
            if (nestedInteger.isInteger()) {
                queue.offer(nestedInteger.getInteger());
            } else {
                initQueue(nestedInteger.getList());
            }
        }
    }

    @Override
    public Integer next() {
        return queue.poll();
    }

    @Override
    public boolean hasNext() {
        return !queue.isEmpty();
    }

}
```

[맨위로](#coding-interview)

## Tree
### Symmetric Tree(대칭 트리)
이진 트리의 루트가 주어지면 대칭 트리인지 확인합니다.   
(즉, 중앙을 중심으로 대칭이 됩니다.)

**input**
* 트리의 노드 수는 [1, 1000] 범위에 있습니다.
* -100 <= Node.val <= 100
* 재귀와 반복 두 가지 방법으로 풀어야 합니다.

**example**
```
Input: root = [1,2,2,3,4,4,3]
Output: true
```

**풀이**   
반복문 사용
```
public boolean isSymmetric(TreeNode root) {
    if (root.left == null && root.right == null) { // 노드가 1개이면 true 리턴
        return true;
    }

    Stack<TreeNode> stack = new Stack<>();
    stack.push(root.left);
    stack.push(root.right);

    while (!stack.isEmpty()) {
        TreeNode right = stack.pop();
        TreeNode left = stack.pop();

        if ((left == null && right != null) || (left != null && right == null)) { // 한쪽만 null이면 false
            return false;
        } else if (left != null && right != null) { // 둘다 null이면 바로 다음 stack 반복
            if (left.val != right.val) { // 둘다 null이 아니면 값 비교
                return false;
            }

            // left의 left, right의 right를 push (대칭)
            stack.push(left.left);
            stack.push(right.right);

            // left의 right, right의 left를 push (대칭)
            stack.push(left.right);
            stack.push(right.left);
        }
    }

    return true;
}
```

재귀 사용
```
public boolean isSymmetric(TreeNode root) {
    return recursion(root.left, root.right); // 재귀 호출
}

private boolean recursion(TreeNode left, TreeNode right) {
    if ((left == null && right != null) || (left != null && right == null)) { // 둘 중 하나만 null이면 false
        return false;
    }

    if (left == null && right == null) { // 둘다 null이면 true
        return true;
    }

    if (left.val == right.val) { // 둘의 값이 같으면 left의 left와 right의 right 재귀호출 && left의 right와 right의 left 재귀 호출 (대칭)
        return recursion(left.left, right.right) && recursion(left.right, right.left);
    }

    return false; // 둘의 값이 다르면 false
}
```

[맨위로](#coding-interview)

### Maximum Depth of Binary Tree(이진 트리의 최대 깊이)
이진 트리의 루트가 주어지면 최대 깊이를 반환합니다.   

이진 트리의 최대 깊이는 루트 노드에서 가장 먼 리프 노드까지 가장 긴 경로를 따라가는 노드 수입니다.   

**input**
* 트리 노드의 수는 [0, 104] 범위에 있습니다.
* -100 <= Node.val <= 100

**example**
```
Input: root = [3,9,20,null,null,15,7]
Output: 3
```

**풀이**    
```
public int maxDepth(TreeNode root) {
    if (root == null) { // root가 null이면 0 리턴
        return 0;
    }

    return 1 + Math.max(maxDepth(root.left), maxDepth(root.right)); // left와 right 끝까지 갔다가 돌아오면서 max 값 + 1 리턴 
}
```

[맨위로](#coding-interview)

## Heap
### Kth Largest Element in an Array(배열에서 k번째로 큰 요소)
정수 배열 nums와 정수 k가 주어지면 배열에서 k번째로 큰 요소를 반환합니다.

이 요소는 k번째 요소가 아니라 정렬된 순서에서의 k번째로 큰 요소입니다.

**input**
* 1 <= k <= nums.length <= 104
* -104 <= nums[i] <= 104

**example**
```
Input: nums = [3,2,1,5,6,4], k = 2
Output: 5
=======

>>>>>>> 538fb899f7bb11f81f49ff6ee41107dc97d5f1e2
```

**풀이**
```
public int findKthLargest(int[] nums, int k) {
    PriorityQueue<Integer> priorityQueue= new PriorityQueue<>(); // Min Heap 생성

    for (int i = 0; i < nums.length; i++){
        priorityQueue.add(nums[i]);
        if (priorityQueue.size() > k) { // heap의 사이즈가 k보다 크면 최소값을 제거한다.
            priorityQueue.remove();
        }
    }

    return priorityQueue.remove(); // 마지막엔 가장 큰 k개의 수만 heap에 남아있게 되므로 남은 값 중 최소값을 반환한다.
```

[맨위로](#coding-interview)

### Top K Frequent Elements(빈도 높은 요소 Top K)
정수 배열 nums와 정수 k가 주어지면 가장 빈도가 높은 요소 k개를 반환합니다.   
답의 순서는 상관없습니다.

**input**
* 1 <= nums.length <= 105
* k는 [1, 배열에 포함된 고유한 요소의 갯수] 범위에 있습니다.
* 정답은 고유합니다.

**example**
```
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

**풀이**
```
public int[] topKFrequent(int[] nums, int k) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int num : nums) { // Map에 숫자와 빈도수를 저장한다.
        map.put(num, map.getOrDefault(num, 0) + 1);
    }

    PriorityQueue<Map.Entry<Integer, Integer>> queue = new PriorityQueue<>((a, b) -> { // Max Heap 생성, Map은 Entry로 넣어야 한다.
        return b.getValue() - a.getValue();
    });

    for (Map.Entry<Integer, Integer> entry : map.entrySet()) {
        queue.offer(entry);
    }

    int[] result = new int[k];
    for (int i = 0; i < k; i++) { // k개 만큼 key를 가져와서 결과에 저장
        result[i] = queue.poll().getKey();
    }

    return result;

```

[맨위로](#coding-interview)

## Graph
### Course Schedule(강의 일정)
0부터 numCours - 1까지 총 numCours개의 강의를 수강해야 합니다.
ai 강의를 수강하려면 bi 강의를 먼저 수강해야한다는 전제조건이 prerequisites[i] = [ai, bi]로 주어집니다.   
* 예를 들어 pair[0, 1]는 0 강의를 수강하려면 1 강의를 먼저 수강해야한다는 전제조건입니다.   

모든 강의를 수강할 수 있는 경우 true를 반환합니다.   
그렇지 않으면 false를 반환합니다.

**input**
* 1 <= numCourses <= 105
* 0 <= prerequisites.length <= 5000
* prerequisites[i].length == 2
* 0 <= ai, bi < numCourses
* 모든 prerequisites[i] 쌍은 고유합니다.

**example**
```
Input: numCourses = 2, prerequisites = [[1,0]]
Output: true
Explanation: There are a total of 2 courses to take. 
To take course 1 you should have finished course 0. So it is possible.
```

**풀이**
```
public boolean canFinish(int numCourses, int[][] prerequisites) {
    int[][] matrix = new int[numCourses][numCourses]; // x: 강의 번호, y: x 강의를 사전에 들어야 들을 수 있는 강의의 번호
    int[] preCountArray = new int[numCourses]; // 각 강의를 듣기 위해 들어야하는 사전 강의 수

    for (int[] pair : prerequisites) {
        int before = pair[1];
        int after = pair[0];
        matrix[before][after] = 1;
        preCountArray[after]++;
    }

    Queue<Integer> queue = new LinkedList<>();
    for (int i = 0; i < numCourses; i++) {  // 사전 강의가 필요 없는 강의들을 먼저 queue에 담는다.
        if (preCountArray[i] == 0) {
            queue.offer(i);
        }
    }

    int count = 0;
    while (!queue.isEmpty()) {
        int course = queue.poll();
        count++;
        for (int i = 0; i < numCourses; i++) {
            if (matrix[course][i] == 1) { // course를 들었으니 i 강의의 사전 강의 수를 1개 감소시킨다.
                preCountArray[i]--;
                if (preCountArray[i] == 0) { // i강의의 사전 강의 수가 0이 되면 이제 수강할 수 있으므로 queue에 넣어준다.
                    queue.offer(i);
                }
            }
        }
    }

    return count == numCourses; // 지금까지 수강한 강의 수 count와 numCourses의 값이 같은지 여부를 리턴한다.
}
```

[맨위로](#coding-interview)

### Course Schedule II(강의 일정 2)
0부터 numCours - 1까지 총 numCours개의 강의를 수강해야 합니다.   
ai 강의를 수강하려면 bi 강의를 먼저 수강해야한다는 전제조건이 prerequisites[i] = [ai, bi]로 주어집니다.   
* 예를 들어 pair[0, 1]는 0 강의를 수강하려면 1 강의를 먼저 수강해야한다는 전제조건입니다.   

모든 강의를 수강하기 위한 강의 순서를 반환합니다.   
유효한 답이 많으면 그 중 하나만 반환하면 됩니다.   
모든 강의를 완료할 수 없는 경우 빈 배열을 반환합니다.   

**input**
* 1 <= numCourses <= 2000
* 0 <= prerequisites.length <= numCourses * (numCourses - 1)
* prerequisites[i].length == 2
* 0 <= ai, bi < numCourses
* ai != bi
* 모든 [ai, bi]쌍은 구별됩니다.

**example**
```
Input: numCourses = 2, prerequisites = [[1,0]]
Output: [0,1]
Explanation: There are a total of 2 courses to take. To take course 1 you should have finished course 0. So the correct course order is [0,1].
```

**풀이**
```
// 기본적인 로직은 Course Schedule 풀이와 같습니다.
public int[] findOrder(int numCourses, int[][] prerequisites) {
    int[][] matrix = new int[numCourses][numCourses];
    int[] preCourseCount = new int[numCourses];

    for (int[] pair : prerequisites) {
        int prev = pair[1];
        int ready = pair[0];
        matrix[prev][ready] = 1;
        preCourseCount[ready]++;
    }

    Queue<Integer> queue = new LinkedList<>();
    for (int i = 0; i < numCourses; i++) {
        if (preCourseCount[i] == 0) {
            queue.offer(i);
        }
    }

    int[] result = new int[numCourses]; // 결과 배열
    int resultIndex = 0; // 결과를 담을 index
    while (!queue.isEmpty()) {
        int course = queue.poll();
        result[resultIndex++] = course; // 결과에 하나씩 추가
        for (int i = 0; i < numCourses; i++) {
            if (matrix[course][i] == 1) {
                preCourseCount[i]--;
                if (preCourseCount[i] == 0) {
                    queue.offer(i);
                }
            }
        }
    }

    return resultIndex == numCourses ? result : new int[0]; // 결과 배열이 모두 채워졌으면 result를 리턴, 아니면 빈 배열을 리턴합니다.
}
```

[맨위로](#coding-interview)

## HashTable
### Roman to Integer(로마 숫자를 정수로 변환)
로마 숫자는 7가지 기호로 표시됩니다. : I, V, X, L, C, D, M.
```
Symbol       Value
I             1
V             5
X             10
L             50
C             100
D             500
M             1000
```
예를 들어, 2는 로마 숫자에서 II로 쓰이고 I 2개가 합쳐진 것입니다.   
12는 XII로 쓰이고 X + II 입니다.   
27은 XXVII로 쓰이고 XX + V + II 입니다.   

로마 숫자는 보통 왼쪽에서 오른쪽으로 큰 숫자부터 작은 숫자로 쓰입니다.   
그러나 4는 IIII가 아닙니다.   
대신에 4는 IV로 쓰입니다.   
왜냐하면 4를 만들기 위해 5에서 1을 빼면되기 때문입니다.
같은 원리가 IX로 쓰여지는 9에도 적용됩니다.   
이와 같은 원리가 사용되는 6가지 예시 입니다.
* I는 V(5)와 X(10) 앞에 배치되어 4와 9를 만들 수 있습니다.
* X는 L(50)과 C(100) 앞에 배치되어 40과 90을 만들 수 있습니다.
* C는 D(500)과 M(1000) 앞에 배치되어 400과 900을 만들 수 있습니다.

로마 숫자가 주어지면 정수로 변환합니다.   

**input**
* 1 <= s.length <= 15
* s에는 문자 ('I', 'V', 'X', 'L', 'C', 'D', 'M')만 포함됩니다.
* s는 [1, 3999] 범위의 유효한 로마 숫자임이 보장됩니다.

**example**
```
Input: s = "III"
Output: 3
```

**풀이**
```
public int romanToInt(String s) {
    Map<Character, Integer> map = new HashMap<>(); // 로마 숫자 map에 저장
    map.put('I', 1);
    map.put('V', 5);
    map.put('X', 10);
    map.put('L', 50);
    map.put('C', 100);
    map.put('D', 500);
    map.put('M', 1000);

    int length = s.length();
    int result = map.get(s.charAt(length - 1)); // 가장 오른쪽 숫자를 결과에 저장
    for (int i = length - 2; i >= 0; i--) {
        if (map.get(s.charAt(i)) >= map.get(s.charAt(i + 1))) { // 오른쪽 숫자보다 크면 더한다.
            result += map.get(s.charAt(i));
        } else { // 오른쪽 숫자보다 작으면 뺀다.
            result -= map.get(s.charAt(i));
        }
    }

    return result;
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

**example**
```
Input: head = [3,2,0,-4], pos = 1
Output: true
Explanation: There is a cycle in the linked list, where the tail connects to the 1st node (0-indexed).
```

**풀이**
```
public boolean hasCycle(ListNode head) {
    Set<ListNode> set = new HashSet<>();
    ListNode current = head;
    while (current != null) {
        if (set.contains(current)) { // set에 있으면 cycle이므로 true 리턴
            return true;
        }

        set.add(current); // 없으면 set에 추가
        current = current.next;
    }

    return false; // 다 돌때 까지 true가 아니기 때문에 false 리턴
}
```

[맨위로](#coding-interview)

## recursion
### Reverse Linked List(링크드 리스트 뒤집기)
단일 링크드 리스트 head가 주어지면 뒤집어서 반환합니다.   

**input**
* 리스트의 노드 수는 [0, 5000] 범위에 있습니다.
* -5000 <= Node.val <= 5000
* 재귀로 구현합니다.

**example**
```
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

**풀이**
```
public ListNode reverseList(ListNode head) {
    return recursion(head, null);
}

private ListNode recursion(ListNode node, ListNode prevNode) {
    if (node == null) { // node가 null이면 prevNode가 새로운 head가 되어 리턴된다.
        return prevNode;
    }

    ListNode next = node.next; // 다음 노드를 임시로 저장해둔다.
    node.next = prevNode; // 현재 노드의 다음 노드를 이전 노드를 가리키게 한다.
    return recursion(next, node); // next 노드(현재 노드가 됨)와 현재노드(이전 노드가 됨)를 전달하여 함수를 호출한다.
}
```

[맨위로](#coding-interview)

### Palindrome Linked List(회문 링크드 리스트)
단일 링크드 리스트의 head가 주어지고 해당 리스트가 회문이면 true를 반환합니다.
> 회문(palindrome): 앞에서 읽으나 뒤에서 읽으나 같은 것

**input**
* 리스트 노드의 수는 [1, 105] 범위에 있습니다.
* 0 <= Node.val <= 9

**example**
```
Input: head = [1,2,2,1]
Output: true
```

**풀이**
```
public boolean isPalindrome(ListNode head) {
    if (head == null) { // 리스트의 끝까지 간 후 초기 결과 true로 세팅한다.
        return true;
    }

    if (node == null) { // head 노드를 저장해 둔다.
        node = head;
    }

    boolean bool = isPalindrome(head.next); // 꼬리까지 간다. 꼬리까지 간 후 돌아왔을때 초기 bool은 true

    if (head.val == node.val) {    // 처음 head는 꼬리이며, node는 헤드이다. 값을 비교하여 같으면 node를 한칸 옮긴다.
        node = node.next;
    } else { // 같지 않으면 false를 리턴한다.
        bool = false;
    }

    return bool;
}
```

[맨위로](#coding-interview)

## Backtracking
### Letter Combinations of a Phone Number(전화번호의 문자 조합)
2~9의 숫자가 포함된 문자열이 주어지면 숫자가 나타낼 수 있는 모든 가능한 문자 조합을 반환합니다.   
순서에 관계없이 답을 반환합니다.   

전화 버튼과 마찬가지로 숫자와 문자 매핑이 아래에 나와 있습니다.   
1은 어떤 문자에도 매핑되지 않습니다.   

**input**
* 0 <= digits.length <= 4
* digits[i]는 ['2', '9'] 범위의 숫자입니다.

**example**
```
Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

**풀이**
```
private String[] array = new String[]{"", "", "abc", "def", "ghi", "jkl", "mno", "pqrs", "tuv", "wxyz"};

public List<String> letterCombinations(String digits) {
    List<String> resultList = new ArrayList<>();

    if (digits.length() > 0) { // 입력 값이 "" 이면 빈 리스트 리턴
        backTracking(resultList, digits, 0, "");
    }

    return resultList;
}

private void backTracking(List<String> resultList, String digits, int index, String combination) {
    if (index == digits.length()) { // index 값이 digits의 길이와 같으면 결과에 추가하고 리턴한다.
        resultList.add(combination);
        return;
    }

    String str = array[digits.charAt(index) - '0']; // 현재 숫자를 가져온다.
    for (char c : str.toCharArray()) { // 현재 숫자에 포함된 문자들을 순회하며 백트래킹을 진행한다.
        backTracking(resultList, digits, index + 1, combination + c);
    }
}
```

[맨위로](#coding-interview)

### Generate Parentheses(괄호 생성)
n 괄호 쌍이 주어지면 잘 구성된 괄호의 모든 조합을 생성하는 함수를 작성합니다.

**input**
* 1 <= n <= 8

**example**
```
Input: n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]
```

**풀이**
```
public List<String> generateParenthesis(int n) {
    List<String> resultList = new ArrayList<>();
    backTracking(resultList, "", 0, 0, n);

    return resultList;
}

private void backTracking(List<String> resultList, String str, int open, int close, int n) {
    if (str.length() == n * 2) { // 문자열이 n * 2이면 완성된 것이므로 리스트에 추가한다.
        resultList.add(str);
        return;
    }

    if (open < n) { // open이 n보다 작으면 추가할 수 있다.
        backTracking(resultList, str + "(", open + 1, close, n);
    }

    if (close < open) { // close는 open보다 작아야 추가할 수 있다.
        backTracking(resultList, str + ")", open, close + 1, n);
    }
}
```

[맨위로](#coding-interview)

## Dynamic Programming
### Maximum Subarray(부분배열 합의 최대값)
정수 배열 nums가 주어지면 가장 큰 합을 가지는 연속적인 부분배열(최소한 하나의 숫자를 포함)을 찾아 그 합을 반환합니다.   

**input**
* 1 <= nums.length <= 3 * 10^4
* -105 <= nums[i] <= 105

**example**
```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: [4,-1,2,1]이 가장 큰 합 = 6입니다.
```

**풀이**
```
public int maxSubArray(int[] nums) {
    int max = nums[0]; // 결과로 반환할 최대값
    int prevMaxSum = nums[0]; // 이전 배열 값의 최대값
    for (int i = 1; i < nums.length; i++) {
        prevMaxSum = Math.max(nums[i], nums[i] + prevMaxSum); // 이전 배열 값의 최대값을 구한다. (현재 값과 (이전 값 + 현재값) 중 최대값)
        max = Math.max(prevMaxSum, max); // 결과로 반활할 최대값을 새로 저장한다.
    }

    return max; // 최대값 반환
}
```

[맨위로](#coding-interview)

### Climbing Stairs(계단 오르기)
당신은 계단을 오르고 있습니다.   
정상 n에 도달하려면 단계가 필요합니다.   

매번 1개 또는 2개 오를 수 있습니다.   
정상에 오를 수 있는 모든 경우의 수를 반환합니다.   

**input**
* 1 <= n <= 45

**example**
```
Input: n = 2
Output: 2
Explanation: 정상에 오르는 방법에는 두 가지가 있습니다. 
1. 1 step + 1 step
2. 2 steps
```

**풀이**
```
public int climbStairs(int n) {
    if (n <= 2) { // 2개 까지는 n 반환
        return n;
    }
    int[] dp = new int[n + 1];
    dp[1] = 1;
    dp[2] = 2;
    for (int i = 3; i <= n; i++) { // (dp[i - 2] 계단에서 +2로 오는 경우) + (dp[i - 1] 계단에서 +1로 오는 경우)
        dp[i] = dp[i - 2] + dp[i - 1];
    }

    return dp[n];
}
```

[맨위로](#coding-interview)

## Sorting
### Merge Sorted Array(배열의 병합 정렬)
오름차순으로 정렬된 두 정수 배열 nums1, nums2과 각 배열의 요소 수를 나타내는 두 정수 m과 n이 주어집니다.   

nums1과 nums2를 오름차순으로 병합 정렬합니다.  

최종 정렬된 배열은 함수에 의해 반환되지 않고 대신 nums1 배열 내부에 저장 되어야 합니다.    
이를 수용하기 위해 nums1 배열의 길이는 m + n이고, 첫번째 부터 요소 m개는 병합해야 하는 요소를 나타냅니다.   
그리고 마지막 n개의 요소는 0으로 설정되며 무시해야 합니다.   
nums2의 길이는 n 입니다.   

**input**   
* nums1.length == m + n
* nums2.length == n
* 0 <= m, n <= 200
* 1 <= m + n <= 200
* -109 <= nums1[i], nums2[j] <= 109
* 시간 복잡도 O(m + n)으로 구현합니다.

**example**
```
Input: nums1 = [1,2,3,0,0,0], m = 3, nums2 = [2,5,6], n = 3
Output: [1,2,2,3,5,6]
Explanation: 병합할 배열은 [1,2,3] 및 [2,5,6]입니다. 
병합 결과는 [ 1 , 2 ,2, 3 ,5,6] 입니다.
```

**풀이**
```
public void merge(int[] nums1, int m, int[] nums2, int n) {
    int tail1 = m - 1; // nums1의 끝 index
    int tail2 = n - 1; // nums2의 끝 index
    int finished = m + n - 1; // 결과 배열의 끝 index

    while (tail1 >= 0 && tail2 >= 0) {
        nums1[finished--] = (nums1[tail1] > nums2[tail2]) ? nums1[tail1--] : nums2[tail2--]; // 끝부터 큰 숫자를 순차적으로 넣는다.
    }

    while (tail2 >= 0) { // tail2가 남았으면 나머지 배열에 넣는다. 이 때 tail2는 안남고 tail1만 남았으면 nums1을 리턴하는 것이기 때문에 추가 작업 없이 남겨두면 된다.
        nums1[finished--] = nums2[tail2--];
    }
}
```

[맨위로](#coding-interview)

### Majority Element(과반수 요소)
n 크기의 배열 nums가 주어지면 과반수 요소를 반환합니다.      
과반수 요소는 여러 ⌊n / 2⌋번 이상 나타나는 요소입니다 .   
과반수 요소가 항상 배열에 존재한다고 가정할 수 있습니다.   

**input**
* n == nums.length
* 1 <= n <= 5 * 104
* -231 <= nums[i] <= 231 - 1

**example**
```
Input: nums = [3,2,3]
Output: 3
```

**풀이**
```
public int majorityElement(int[] nums) {
    Arrays.sort(nums); // 배열을 정렬한다.
    return nums[nums.length / 2]; // majority 수는 length / 2 개 이상 있기 때문에 정렬을 하게 되면 항상 중간 요소의 값이 된다.
}
```

[맨위로](#coding-interview)

## Binary Search
### Sqrt(x)(제곱근 x)
음이 아닌 정수 n이 주어지면, 제곱근 x를 구하여 반환합니다.   

반환 유형이 정수이므로 소수 자릿수가 잘리고 결과의 정수 부분만 반환됩니다.   

참고: 내장된 라이브러리를 사용할 수 없습니다.    
ex) pow(x, 0.5)

**input**
* 0 <= x <= 2^31 - 1

**example**
```
Input: x = 4
Output: 2
```

**풀이**
```
public int mySqrt(int x) {
    if (x == 0) { // x == 0이면 0 반환
        return 0;
    }

    int start = 1; // x > 0이면 정답은 0보다 크기 때문에 start를 1로 잡는다.
    int end = x;
    while (start <= end) {
        int mid = (start + end) / 2; // 중간 값
        if (mid <= x / mid && (mid + 1) > x / (mid + 1)) {// 결과 조건
            return mid;
        } else if (mid > x / mid) {
            end = mid - 1;
        } else {
            start = mid + 1;
        }
    }

    return start;
}
```

[맨위로](#coding-interview)

### Intersection of Two Arrays II(두 배열의 교집합 2)
두 정수 배열 nums1과 nums2가 주어지면 두 배열의 교집합 배열을 반환합니다.   
결과의 각 요소는 두 배열에 모두 표시되는 횟수만큼 나타나야 하며 원하는 순서로 결과를 반환할 수 있습니다.  

**input**
* 1 <= nums1.length, nums2.length <= 1000
* 0 <= nums1[i], nums2[i] <= 1000

**풀이**
```
public int[] intersect(int[] nums1, int[] nums2) {
    Arrays.sort(nums1); // nums1을 오름차순 정렬
    List<Integer> nums1List = new ArrayList<>();
    for (int num : nums1) { // ArrayList에 담는다.
        nums1List.add(num);
    }

    List<Integer> ret = new ArrayList<>();
    for (int num: nums2) {
        int idx = search(nums1List, num); // 이진 탐색
        if (idx != -1) {  // nums1List에 있으면 ret에 추가
            nums1List.remove(idx); // 추가 했으니 nums1List에서 제거한다.
            ret.add(num);
        }
    }

    int[] retArr = new int[ret.size()];
    int i = 0;
    for (int num : ret) { // ret를 retArr배열로 옮겨 담는다.
        retArr[i++] = num;
    }

    return retArr;
}

public int search(List<Integer> nums, int key) { // 이진 탐색
    int high = nums.size() - 1;
    int low = 0;

    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (nums.get(mid) == key) {
            return mid;
        } else if (nums.get(mid) > key) {
            high = mid - 1;
        } else {
            low = mid + 1;
        }
    }

    return -1;
}
```

[맨위로](#coding-interview)

## DFS
### Binary Tree Inorder Traversal(이진 트리 중위 순회)
이진 트리의 루트가 주어지면 노드의 값을 중위 순회로 반환합니다.   

**input**
* 트리의 노드 수 범위는 [0, 100] 입니다..
* -100 <= Node.val <= 100

**example**
```
Input: root = [1,null,2,3]
Output: [1,3,2]
```

**풀이**
```
public List<Integer> inorderTraversal(TreeNode root) {
    List<Integer> resultList = new ArrayList<>();
    dfs(root, resultList);

    return resultList;
}

private void dfs(TreeNode root, List<Integer> resultList) { // dfs 로직
    if (root != null) {
        if (root.left != null) {
            dfs(root.left, resultList); // 왼쪽 노드 먼저 재귀
        }

        resultList.add(root.val); // 현재 노드 추가
        
        if (root.right != null) {
            dfs(root.right, resultList); // 오른쪽 노드 재귀
        }
    }
}
```

[맨위로](#coding-interview)

### Symmetric Tree(대칭 트리)
이진 트리의 루트가 주어지면 대칭 트리인지 확인합니다.   
(즉, 중앙을 중심으로 대칭이 됩니다.)

**input**
* 트리의 노드 수는 [1, 1000] 범위에 있습니다.
* -100 <= Node.val <= 100

**example**
```
Input: root = [1,2,2,3,4,4,3]
Output: true
```

**풀이**
```
public boolean isSymmetric(TreeNode root) {
    return dfs(root.left, root.right);
}

private boolean dfs(TreeNode left, TreeNode right) {
    if (left == null && right == null) { // 둘다 null이면 true
        return true;
    }

    if ((left == null && right != null) || (left != null && right == null)) { // 한쪽만 null이면 false
        return false;
    }

    if (left.val != right.val) { // 둘다 null이 아니지만 val이 다르면 false
        return false;
    }

    return dfs(left.left, right.right) && dfs(left.right, right.left); // 자식 노드 dfs 호출
}
```

[맨위로](#coding-interview)

## BFS
### Symmetric Tree(대칭 트리)
이진 트리의 루트가 주어지면 대칭 트리인지 확인합니다.   
(즉, 중앙을 중심으로 대칭이 됩니다.)

**input**
* 트리의 노드 수는 [1, 1000] 범위에 있습니다.
* -100 <= Node.val <= 100

**example**
```
Input: root = [1,2,2,3,4,4,3]
Output: true
```

**풀이**
```
public boolean isSymmetric(TreeNode root) {
    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root.left);
    queue.offer(root.right);

    while (!queue.isEmpty()) {
        TreeNode left = queue.poll();
        TreeNode right = queue.poll();

        if ((left == null && right != null) || (left != null && right == null)) {
            return false;
        }

        if (left != null && right != null) {
            if (left.val != right.val) {
                return false;
            }

            queue.offer(left.left);
            queue.offer(right.right);
            queue.offer(left.right);
            queue.offer(right.left);
        }
    }

    return true;
}
```

[맨위로](#coding-interview)

### Maximum Depth of Binary Tree(이진 트리의 최대 깊이)
이진 트리의 루트가 주어지면 최대 깊이를 반환합니다.   

이진 트리의 최대 깊이는 루트 노드에서 가장 먼 리프 노드까지 가장 긴 경로를 따라가는 노드 수입니다.   

**input**
* 트리 노드의 수는 [0, 104] 범위에 있습니다.
* -100 <= Node.val <= 100

**example**
```
Input: root = [3,9,20,null,null,15,7]
Output: 3
```

**풀이**
```
public int maxDepth(TreeNode root) {
    if (root == null) {
        return 0;
    }

    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);

    int maxDepth = 0;
    while (!queue.isEmpty()) {
        int qSize = queue.size();
        while (qSize-- > 0) { // 현재까지 queue에 들어있는 node들의 depth는 모두 같다.
            TreeNode node = queue.poll();
            if (node.left != null) {
                queue.offer(node.left);
            }

            if (node.right != null) {
                queue.offer(node.right);
            }
        }

        maxDepth++; // depth를 1 증가시킨다.
    }

    return maxDepth;
}
```

[맨위로](#coding-interview)

## Bit Manipulation
### Single Number(1개만 존재하는 수 찾기)
비어있지 않은 정수 배열 nums가 주어지고, 하나를 제외하고 모든 요소는 두 번씩 존재합니다.   
하나만 존재하는 수를 찾습니다.   

시간복잡도 O(n)으로 구현합니다.   

**input**
* 1 <= nums.length <= 3 * 10^4
* -3 * 10^4 <= nums[i] <= 3 * 10^4
* 배열의 각 요소는 한 번만 나타나는 하나의 요소를 제외하고 두 번 나타납니다.

**example**
```
Input: nums = [2,2,1]
Output: 1
```

**풀이**
```
public int singleNumber(int[] nums) {
    int result = 0;
    for (int num : nums) {
        result ^= num; // XOR은 자기 자신과 같은 숫자랑 연산할 경우 0이되고, 0이랑 연산하면 자기 자신이 된다.
    }

    return result;
}
```

[맨위로](#coding-interview)

### Reverse Bits(비트 뒤집기)
주어지는 32비트 unsigned integer를 뒤집습니다.   

* Java와 같은 일부 언어에는 unsigned integer 유형이 없습니다.   
이 경우 입력과 출력 모두 signed integer 유형으로 제공됩니다.   
정수의 내부 이진 표현은 signed이든 unsigned이든 동일하므로 구현에 영향을 주지 않아야 합니다.   
* Java에서 컴파일러는 2의 보수 표기법을 사용하여 signed integer를 나타냅니다.    

**input**
* 입력은 길이 32의 이진 문자열이어야 합니다.

**example**
```
Input: n = 11111111111111111111111111111101
Output:   3221225471 (10111111111111111111111111111111)
Explanation: 입력 이진 문자열 11111111111111111111111111111101는 부호없는 정수 4294967293이고, 그래서 3221225471(이진 표현=10111111111111111111111111111111)을 반환합니다.
```

**풀이**
```
public int reverseBits(int n) {
    if (n == 0) {
        return 0;
    }

    int result = 0;
    for (int i = 0; i < 32; i++) { // 32번 반복
        result <<= 1; // result 비트를 왼쪽으로 1번 이동
        if ((n & 1) == 1) { // n의 1의 자리가 1이면 result에 1을 더한다.
            result++;
        }
        n >>= 1; // n의 다음 비트를 확인하기 위해 오른쪽으로 1번 이동
    }

    return result;
}
```

[맨위로](#coding-interview)

## String
### Longest Common Prefix(가장 긴 공통 접두사)
문자열 배열 중에서 가장 긴 공통 접두사 찾는 함수를 작성합니다.   

공통 접두사가 없으면 빈 문자열 ""을 반환합니다.   

**input**
* 1 <= strs.length <= 200
* 0 <= strs[i].length <= 200
* strs[i]는 영문 소문자로만 구성되어 있습니다.

**example**
```
Input: strs = ["flower","flow","flight"]
Output: "fl"
```

**풀이**
```
public String longestCommonPrefix(String[] strs) {
    String result = strs[0]; // 0번 문자열로 결과 초기화
    for (int i = 1; i < strs.length; i++) {
        while (strs[i].indexOf(result) != 0) { // 접두사 일치하는 문자열 찾을때까지 뒤의 1자리씩 줄이면서 반복
            result = result.substring(0, result.length() - 1);
        }
    }

    return result;
}
```

[맨위로](#coding-interview)

### Implement strStr()(strStr() 구현)
strStr()을 구현합니다.   

haystack에서 처음으로 발견된 needle의 index를 반환하고, 발견되지 않을 경우 -1을 반환합니다.   

needle이 빈 문자열이면 무엇을 반환합니까?    
이것은 인터뷰 중에 물어보는 훌륭한 질문입니다.   

needle이 빈 문자열일 때 0을 반환합니다.   
이것은 C의 strstr() 및 Java의 indexOf()와 일치합니다.   

**input**
* 0 <= haystack.length, needle.length <= 5 * 10^4
* haystack과 needle은 소문자 영어 문자로만 구성되어 있습니다.

**example**
```
Input: haystack = "hello", needle = "ll"
Output: 2
```

**풀이**
```
public int strStr(String haystack, String needle) {
    for (int i = 0; i <= haystack.length() - needle.length(); i++) {
        for (int needleIndex = 0; needleIndex <= needle.length(); needleIndex++) {
            if (needleIndex == needle.length()) {
                return i;
            }

            if (needle.charAt(needleIndex) != haystack.charAt(i + needleIndex)) {
                break;
            }
        }
    }

    return -1;
}
```

[맨위로](#coding-interview)

## 참고
* [LeetCode](https://leetcode.com/problemset/algorithms/)
