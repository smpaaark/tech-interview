# Coding Interview
* [Array](#array)
  * [Two Sum(두 수의 합)](#two-sum두-수의-합)
  * [Remove Duplicates from Sorted Array(정렬된 배열에서 중복 값 제거하기)](#remove-duplicates-from-sorted-array정렬된-배열에서-중복-값-제거하기)
* [참고](#참고)

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

[맨위로](#array)

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

[맨위로](#array)

## 참고
* [LeetCode](https://leetcode.com/problemset/algorithms/)

[맨위로](#array)
