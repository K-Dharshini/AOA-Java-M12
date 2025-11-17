
# EX 2B Jump Game using Greedy Algorithm
## DATE:
## AIM:
To write a Java program to for given constraints. You are given an array of integers. Each number represents the maximum number of steps you can jump forward from that position. You start from the first element (index 0). Write a program to find the minimum number of jumps required to reach the last index of the array. If it is not possible to reach the end, return -1.

## Algorithm
1. **Start** the program and input the number of elements `n`, then read all array values into `nums[]`.
2. **Initialize** variables:  
   - `jumps = 0` to count the number of jumps,  
   - `currentEnd = 0` to mark the current jump boundary,  
   - `farthest = 0` to track how far we can reach.
3. **Traverse** the array until the second last element, updating `farthest` as the maximum reachable index from the current range.
4. **Check** if the current index reaches `currentEnd`; if yes, increment `jumps`, update `currentEnd` to `farthest`, and detect if the end is reachable or if the algorithm is stuck.
5. **Print** the minimum number of jumps if the last index is reachable; otherwise print `-1`, then **stop** the program.  

## Program:
```
Program to implement jump game

Developed by: DHARSHINI K
Register Number: 212223230047

import java.util.Scanner;

public class MinJumpToEnd {

    // Function to return minimum jumps to reach end
    public static int minimumJumps(int[] nums) {
        if (nums.length <= 1) return 0;
        if (nums[0] == 0) return -1;

        int jumps = 0;
        int currentEnd = 0;
        int farthest = 0;

        for (int i = 0; i < nums.length - 1; i++) {
            farthest = Math.max(farthest, i + nums[i]);

            if (i == currentEnd) {
                jumps++;
                currentEnd = farthest;

                if (currentEnd >= nums.length - 1) {
                    break;
                }

                if (currentEnd == i) return -1; // stuck
            }
        }

        return currentEnd >= nums.length - 1 ? jumps : -1;
    }

    // Main method to handle input and output
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(); // Number of elements
        int[] nums = new int[n];

        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        System.out.println("Minimum jumps to reach last index: " + minimumJumps(nums));
    }
}
```

## Output:
<img width="976" height="313" alt="image" src="https://github.com/user-attachments/assets/49c8d409-cd0f-41b3-ab00-2a9e4fbc980a" />

## Result:
The program was successfully implemented and the expected output is verified.
