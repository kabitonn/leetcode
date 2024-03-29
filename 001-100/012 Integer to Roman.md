## [12. Integer to Roman](https://leetcode-cn.com/problems/integer-to-roman/)

## 1. 题目描述\(中等\)

Roman numerals are represented by seven different symbols: I, V, X, L, C, D and M.

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

For example, two is written as II in Roman numeral, just two one's added together. Twelve is written as, XII, which is simply X + II. The number twenty seven is written as XXVII, which is XX + V + II.

Roman numerals are usually written largest to smallest from left to right. However, the numeral for four is not IIII. Instead, the number four is written as IV. Because the one is before the five we subtract it making four. The same principle applies to the number nine, which is written as IX. There are six instances where subtraction is used:

> * I can be placed before V \(5\) and X \(10\) to make 4 and 9. 
> * X can be placed before L \(50\) and C \(100\) to make 40 and 90. 
> * C can be placed before D \(500\) and M \(1000\) to make 400 and 900.
>   Given an integer, convert it to a roman numeral. Input is guaranteed to be within the range from 1 to 3999.

Example 1:

```
Input: 3
Output: "III"
```

Example 2:

```
Input: 4
Output: "IV"
```

Example 3:

```
Input: 9
Output: "IX"
```

Example 4:

```
Input: 58
Output: "LVIII"
```

> Explanation: L = 50, V = 5, III = 3.

Example 5:

```
Input: 1994
Output: "MCMXCIV"
```

> Explanation: M = 1000, CM = 900, XC = 90 and IV = 4.

## 2. 思路

1. 最大的依此减去当前包含最大的值对应的字符
2. 直接对每一位数字转换为对应的字符

## 3. 解决方法

### 3.1

```java
    public String intToRoman(int num) {
        StringBuilder sb = new StringBuilder();
        int[] values = {1000,900,500,400,100,90,50,40,10,9,5,4,1};
        String[] strings = {"M","CM","D","CD","C","XC","L","XL","X","IX","V","IV","I"};
        for(int i=0;i<values.length;i++) {
            while(num>=values[i]) {
                sb.append(strings[i]);
                num-=values[i];
            }

        }
        return sb.toString();
    }
```

### 3.2

```java
   public String intToRoman(int num) {
        String M[] = {"", "M", "MM", "MMM"};//0,1000,2000,3000
        String C[] = {"", "C", "CC", "CCC", "CD", "D", "DC", "DCC", "DCCC", "CM"};//0,100,200,300...
        String X[] = {"", "X", "XX", "XXX", "XL", "L", "LX", "LXX", "LXXX", "XC"};//0,10,20,30...
        String I[] = {"", "I", "II", "III", "IV", "V", "VI", "VII", "VIII", "IX"};//0,1,2,3...
        return M[num/1000] + C[(num%1000)/100]+ X[(num%100)/10] + I[num%10];
    }
```



