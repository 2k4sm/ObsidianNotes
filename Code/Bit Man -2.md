## Single Number II

	
Given an array of integers, every element appears thrice except for one, which occurs once.
	
Find that element that does not appear thrice.
	
NOTE: Your algorithm should have a linear runtime complexity.
	
Could you implement it without using extra memory?
	
A = [1,2,4,3,3,2,2,,3,1,1]
	
	1 -> 0 0 1
	2 -> 0 1 0
	4 -> 1 0 0
	3 -> 0 1 1
	3 -> 0 1 1
	2 -> 0 1 0
	2 -> 0 1 0
	3 -> 0 1 1
	1 -> 0 0 1
	1 -> 0 0 1
	
```
//java
public int singleNumber(final List<Integer> A) {
        int num = 0;
        for (int i = 0; i < 32;i++){
            int bitcount = 0;
            for (int j : A){
                j = j >> i;
                bitcount += (j & 1);
            }
            if (bitcount % 3  != 0){
                num = num | (1 << i);
            }else{
                num = num | (0 << i);
            }
        }

        return num;
    }
```


## Single Number III

Given an array of positive integers A, two integers appear only once, and all the other integers appear twice.
Find the two integers that appear only once.

Note: Return the two numbers in ascending order.

A = [1, 2, 3, 1, 2, 4]

1 -> 0 0 1
2 -> 0 1 0
3 -> 0 1 1
1 -> 0 0 1
2 -> 0 1 0
4 -> 1 0 0

B = [3,4,5,7,6,3,6,5,8,4]

3 -> 0 0 1 1
4 -> 0 1 0 0
5 -> 0 1 0 1
7 -> 0 1 1 1
6 -> 0 1 1 0
3 -> 0 0 1 1
6 -> 0 1 1 0
5 -> 0 1 0 1
8 -> 1 0 0 0