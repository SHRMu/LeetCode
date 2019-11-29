- [x] 1. [Two Sum](#two_sum)
- [x] 2. [Add Two Numbers](#add_two_numbers)
- [x] 3.  [longest Substring Without Repeating Characters](#lengthOfLongestSubstring)
- [ ] 5. [Longest Palindromic Substring](#longestPalindrome)


---

##### <span id = "two_sum">1. Two Sum </span>

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

##### <span id = "add_two_numbers">2. Add Two Numbers </span>


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
##### <span id="lengthOfLongestSubstring">3. longest Substring Without Repeating Characters</span>

- Brute Force


```
public int lengthOfLongestSubstring(String s) {
    if (s.equals("") || s == null){return 0;}
    int max = 0;
    for (int i = 0; i < s.length(); i++) {
        Set<Character> set = new HashSet<>();
        set.add(s.charAt(i));
        int num = 1;
        for (int j = i+1; j < s.length(); j++) {
            if (set.contains(s.charAt(j))){
                break;
            }else {
                set.add(s.charAt(j));
                num ++ ;
            }
        }
        if (num > max) max = num;
    }
    return max;
}
```

- Three Points


```
public int lengthOfLongestSubstring(String s) {
    if (s.equals("") || s == null){return 0;}
    int max = 0;
    for (int mid = 0; mid < s.length(); mid ++){
        int left = mid -1;
        int right = mid +1;
        Set<Character> set = new HashSet<>();
        set.add(s.charAt(mid));
        while (left >= 0 && !set.contains(s.charAt(left))){
            set.add(s.charAt(left));
            left --;
        }
        while (right < s.length() && !set.contains(s.charAt(right))){
            set.add(s.charAt(right));
            right ++;
        }
        max = Math.max(right-left-1,max);
    }
    return max;
}
```


##### <span id="longestPalindrome">5. Longest Palindromic Substring</span>
