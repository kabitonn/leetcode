## [204. Count Primes](https://leetcode-cn.com/problems/count-primes/)

## 1. 题目描述(简单)

Count the number of prime numbers less than a non-negative number, n.

Example:
```
Input: 10
Output: 4
Explanation: There are 4 prime numbers less than 10, they are 2, 3, 5, 7.
```


## 2. 思路

## 3. 解决方法

### 3.1 遍历


```java
    public int countPrimes(int n) {
        int count = 0;
        if (n > 2) {
            count++;
        }
        for (int i = 3; i < n; i += 2) {
            if (isPrime(i)) {
                count++;
            }
        }
        return count;
    }

    public boolean isPrime(int n) {
        for (int i = 2; i <= Math.sqrt(n); i++) {
            if (n % i == 0) {
                return false;
            }
        }
        return true;
    }
```

### 3.2


```java
    public int countPrimes1(int n) {
        int count = 0;
        boolean[] notPrime = new boolean[n];
        for (int i = 2; i < n; i++) {
            if (!notPrime[i]) {
                count++;
                for (int j = i * 2; j < n; j += i) {
                    notPrime[j] = true;
                }
            }
        }
        return count;
    }
```


