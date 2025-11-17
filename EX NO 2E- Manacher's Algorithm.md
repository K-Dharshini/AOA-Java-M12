# EX 2E Pattern Matching using Manacher's Algorithm.
## Date:
## Aim:
To write a Java program for the following constraints. Given a string s, return the longest palindromic substring in s using Manacher's algorithm.

## Algorithm
1. **Start** the program and read the input string `s` from the user.
2. **Transform** the string by inserting `#` between characters to handle even-length palindromes uniformly.
3. **Apply Manacher’s Algorithm**:  
   - Use a center and radius to expand palindromes,  
   - Use mirror indices to minimize unnecessary checks,  
   - Store palindrome radii in an array.
4. **Identify** the center with the maximum radius and compute the starting index of the longest palindromic substring in the original string.
5. **Extract and print** the longest palindromic substring using the calculated start position and radius, then **stop** the program.

## Program:
```
Program to implement pattern matching using manacher's algorithm

Developed by: DHARSHINI K
Register Number: 212223230047

import java.util.Scanner;

public class Solution {
    public String longestPalindrome(String s) {
        // Step 1: Transform the string (insert '#')
        StringBuilder sPrime = new StringBuilder("#");
        for (char c : s.toCharArray()) {
            sPrime.append(c).append("#");
        }

        int n = sPrime.length();
        int[] palindromeRadii = new int[n];
        int center = 0;
        int radius = 0;

        // Step 2: Manacher's Algorithm to calculate radii
        for (int i = 0; i < n; i++) {
            int mirror = 2 * center - i;

            if (i < radius) {
                palindromeRadii[i] = Math.min(radius - i, palindromeRadii[mirror]);
            }

            while (
                i + 1 + palindromeRadii[i] < n &&
                i - 1 - palindromeRadii[i] >= 0 &&
                sPrime.charAt(i + 1 + palindromeRadii[i]) == sPrime.charAt(i - 1 - palindromeRadii[i])
            ) {
                palindromeRadii[i]++;
            }

            if (i + palindromeRadii[i] > radius) {
                center = i;
                radius = i + palindromeRadii[i];
            }
        }

        // Step 3: Find the longest palindrome
        int maxLength = 0;
        int centerIndex = 0;
        for (int i = 0; i < n; i++) {
            if (palindromeRadii[i] > maxLength) {
                maxLength = palindromeRadii[i];
                centerIndex = i;
            }
        }

        int startIndex = (centerIndex - maxLength) / 2;
        return s.substring(startIndex, startIndex + maxLength);
    }

    // Main method for user input
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        //System.out.println("Enter a string:");
        String input = scanner.nextLine();

        Solution sol = new Solution();
        String result = sol.longestPalindrome(input);

        System.out.println("Longest Palindromic Substring: " + result);
        scanner.close();
    }
}
```

## Output:
<img width="870" height="203" alt="image" src="https://github.com/user-attachments/assets/cfea247b-7c3e-431d-b6b8-f0e3c1e9da0e" />

## Result:
The program was successfully implemented and the expected output is verified.
