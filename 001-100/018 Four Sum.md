# [18. 4Sum](https://leetcode-cn.com/problems/4sum/)

## 1. 题目描述(中等)

## 2. 思路

## 3. 解决方法

### 3.1



```java
    public List<List<Integer>> fourSum(int[] nums, int target) {
    	List<List<Integer>> tuples = new ArrayList<>();
    	Arrays.sort(nums);
    	for(int i=0;i<nums.length-3;i++) {
    		if(i>0&&nums[i]==nums[i-1]) {
    			continue;
    		}
    		for(int j=nums.length-1;j>=3;j--) {
    			if(j<nums.length-1&&nums[j]==nums[j+1]) {
        			continue;
        		}
    			int low = i+1;
    			int high = j-1;
    			while(low<high) {
    				int sum = nums[i]+nums[j]+nums[low]+nums[high];
    				if(sum==target) {
    					List<Integer> tuple = Arrays.asList(nums[i],nums[low],nums[high],nums[j]);
    					tuples.add(tuple);
    					while(low<high&&nums[low]==nums[low+1]) {
    						low++;
    					}
    					while(low<high&&nums[high]==nums[high-1]) {
    						high--;
    					}
    					low++;
    					high--;
    				}
    				else if (sum<target) {
						low++;
					}
    				else if (sum>target) {
						high--;
					}
    			}
    		}
    	}
    	return tuples;
    }
```







