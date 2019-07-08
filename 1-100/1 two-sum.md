# 001. Two Sum

## 1. 题目描述（简单）

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

Example:

> ```java
> Given nums = [2, 7, 11, 15], target = 9,
> Because nums[0] + nums[1] = 2 + 7 = 9,
> return [0, 1].
> ```

## 2. 解决方法

### 2.1 暴力法-双重循环

 双重循环，遍历所有情况判断相加和是否等于目标target，若符合则返回\(因为唯一存在\)。

```java
    public int[] twoSum(int[] nums, int target) {
        for(int i=0;i<nums.length;i++) {
            for(int j=i+1;j<nums.length;j++) {
                if ((nums[i]+nums[j]) == target) {
                    return new int[] {i,j};
                }
            }
        }
        return null;
    }
```

### 2.2 两遍哈希

第一遍将所有值作为key，索引作为value存入，第二遍判断与目标target之间的差值是否存在，若找到即可返回\(因为唯一存在\)。

```java
    public int[] twoSum2(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for(int i=0;i<nums.length;i++) {
        int complement = target - nums[i];
            if (map.containsKey(complement) && map.get(complement) != i) {
                return new int[] { i, map.get(complement) };
            }
            map.put(nums[i], i);
        }
	return null;
    }
```



