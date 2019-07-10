# [15. 3Sum](https://leetcode-cn.com/problems/3sum/)

## 1. 题目描述(中等)

 
## 2. 思路


## 3. 解决方法

### 3.1 暴力遍历



```java
    public List<List<Integer>> threeSum(int[] nums) {
    	Arrays.sort(nums);
        List<List<Integer>> tuples = new ArrayList<>();
        Set<List<Integer>> set = new HashSet<>();
        int len = nums.length;
        if(len<3)
        	return tuples;
        for(int i=0;i<len-2;i++) {
        	for(int j=i+1;j<len-1;j++) {
        		for(int k=j+1;k<len;k++) {
        			if(nums[i]+nums[j]+nums[k]==0) {
        				List<Integer> tuple = new ArrayList<>();
        				tuple.add(nums[i]);
        				tuple.add(nums[j]);
        				tuple.add(nums[k]);
        				set.add(tuple);
        			}
        		}
        	}
        }
        for (List<Integer> list : set) {
			tuples.add(list);
		}
        return tuples;
    }

```




### 3.2  双指针 set去重



```java
    public List<List<Integer>> threeSum(int[] nums) {
    	List<List<Integer>> tuples = new ArrayList<>();
    	Set<List<Integer>> set = new HashSet<>();
    	Arrays.sort(nums);
    	for(int i=0;i<nums.length-2;i++) {
    		if(i>0&&nums[i]==nums[i-1]) {
    			continue;
    		}
    		int low = i+1;
    		int high = nums.length-1;
    		while(low<high) {
    			int sum = nums[low]+nums[high];
    			if(sum==-nums[i]) {
    				List<Integer> tuple = Arrays.asList(nums[i],nums[low],nums[high]);
    				set.add(tuple);
    				low++;
    				high--;
    			}
    			else if (sum>-nums[i]) {
					high--;
				}
    			else if (sum<-nums[i]) {
    				low++;
				}
    		}
    	}
    	for (List<Integer> list : set) {
			tuples.add(list);
		}
    	return tuples;
    }
```





