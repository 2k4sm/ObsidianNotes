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

Answer


```
public class SmallestXOR {

    public static void main(String[] args) {
        int[] A = {5, 2, 4, 1, 6, 3};

        int xor = 0;
        for (int num : A) {
            xor ^= num;
        }

        int rightmostSetBit = xor & -xor;
        int mask = rightmostSetBit;

        int num1 = 0;
        int num2 = 0;

        for (int num : A) {
            if ((num & mask) == 0) {
                num1 ^= num;
            } else {
                num2 ^= num;
            }
        }

        int[] result = new int[]{Math.min(num1, num2), Math.max(num1, num2)};
        System.out.println(Arrays.toString(result));
    }
}
```

>This code first calculates the XOR of all the numbers in the array. This is done by initializing a variable xor to 0 and then XORing each number in the array with xor. The final value of xor will be the XOR of all the numbers in the array.

>Next, the code finds the rightmost set bit in xor. This is done by performing a bitwise AND operation between xor and its negation, -xor. The result of this operation will be a number with a 1 in the position of the rightmost set bit in xor, and 0s in all other positions.

>The code then creates a mask using the rightmost set bit. This is done by creating a variable mask and initializing it to the rightmost set bit. The mask will be used later to divide the numbers in the array into two groups.

>The code then initializes two variables, num1 and num2, to 0. These variables will be used to store the two numbers that have the smallest XOR value.

>The code then iterates over the numbers in the array. For each number, it performs a bitwise AND operation between the number and the mask. If the result of the AND operation is 0, then the number is placed in the first group. Otherwise, the number is placed in the second group.

>After the iteration is complete, the code calculates the XOR of the numbers in each group and stores the results in num1 and num2. Finally, the code returns a new array containing num1 and num2, with num1 being the smaller of the two numbers.

>This code example illustrates how the approach described above can be used to find the smallest XOR value between two or more numbers. The approach is simple, efficient, and can be used to solve a variety of problems involving XOR.