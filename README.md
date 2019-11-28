- [x] [Two Sum](#two_sum)
- [x] [Add Two Numbers](#add_two_numbers)
- [ ] [longest Substring Without Repeating Characters](#longest_substring)


---

##### <span id = "two_sum"> Two Sum </span>

- Brute Force

```
public int[] twoSum(int[] nums, int target) {
    for (int i = 0; i < nums.length; i++) {
        for (int j = i+1; j < nums.length; j++) {
            if (nums[j] == target-nums[i]){
                return new int[]{i,j};
            }
        }
    }
    return null;
}
```
- HashMap

use hashmap to store nums and index

```
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> map = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        if (map.keySet().contains(target-nums[i])){
            return new int[]{i, map.get(target-nums[i])};
        }else {
            map.put(nums[i],i);
        }
    }
    return null;
}
```

##### <span id = "add_two_numbers"> Add Two Numbers </span>


```
public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
    ListNode l3 = new ListNode(0);
    ListNode tmp = l3;
    int sum = 0;
    int carry = 0;
    while (l1 != null || l2 != null){
        if (l1 != null){
            sum += l1.val;
            l1 = l1.next;
        }
        if (l2 != null){
            sum += l2.val;
            l2 = l2.next;
        }
        sum += carry;
        carry = sum / 10;
        sum = sum % 10;
        tmp.next = new ListNode(sum);
        tmp = tmp.next;
        sum = 0;
    }
    if (carry != 0){
        tmp.next = new ListNode(carry);
    }
    return l3.next;
}
```
##### <span id="longest_substring">longest Substring Without Repeating Characters</span>

