
# EX 2D Pattern Matching using Naive Approach.
## Date:
## Aim:
To write a Java program to for given constraints. Given text string with length n and a pattern with length m, the task is to prints all occurrences of pattern in text.
Note: You may assume that n > m.

**Examples:**

**Input:**  text = "THIS IS A TEST TEXT", pattern = "TEST"  
**Output:** Pattern found at index 10

**Input:**  text = "AABAACAADAABAABA", pattern = "AABA"  
**Output:** Pattern found at index 0, Pattern found at index 9, Pattern found at index 12

## Algorithm
1. **Start** the program and input the main text string and the pattern string from the user.
2. **Calculate** the lengths of the text and pattern, and iterate through the text up to `n - m` positions.
3. **Compare** the pattern with the current substring of the text character by character.
4. **Check** if all characters matched; if yes, print the index where the pattern is found.
5. **Repeat** the process for all positions and **stop** the program. 

## Program:
```
Program to implement pattern matching using naive approach

Developed by: DHARSHINI K
Register Number: 212223230047 

import java.util.Scanner;

public class NaivePatternSearch {
    static void search(String text, String pattern) {
        int n = text.length();
        int m = pattern.length();

        for (int i = 0; i <= n - m; i++) {
            int j;

            // Check for pattern match character by character
            for (j = 0; j < m; j++) {
                if (text.charAt(i + j) != pattern.charAt(j))
                    break;
            }

            // If pattern found
            if (j == m)
                System.out.println("Pattern found at index " + i);
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Taking input from the user
        //System.out.print("Enter the text: ");
        String text = scanner.nextLine();

        //System.out.print("Enter the pattern: ");
        String pattern = scanner.nextLine();

        // Search for pattern in the text
        search(text, pattern);

        scanner.close();
    }
}
```

## Output:
<img width="812" height="267" alt="image" src="https://github.com/user-attachments/assets/58a91e12-0566-4b3b-a4d0-f101804c4899" />

## Result:
The program was successfully implemented and the expected output is verified.
