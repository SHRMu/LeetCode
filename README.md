- [ ] [Two Sum](#two_sum)





---

<span id = "two_sum"> Two Sum </span>

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

