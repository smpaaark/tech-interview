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
* [HashTable]()
  * [Roman to Integer(로마 숫자를 정수로 변환)]()
  * [Linked List Cycle(링크드리스트 싸이클)]()
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

## 참고
* [LeetCode](https://leetcode.com/problemset/algorithms/)

[맨위로](#coding-interview)
