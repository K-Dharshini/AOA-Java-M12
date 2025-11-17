
# EX 2A Assign Cookies using Greedy Algorithm
## Date:
## Aim:
To Write a Java program for the following Constraints. Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie. Each child i has a greed factor g[i], which is the minimum size of a cookie that the child will be content with; and each cookie j has a size s[j]. If s[j] >= g[i], we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximise the number of your content children and output the maximum number.

## Algorithm
1. **Start** the program and input the number of children and cookies, then read their greed factors (`g[]`) and cookie sizes (`s[]`).
2. **Sort** both arrays so that children with the smallest greed and cookies with the smallest sizes are matched first.
3. **Initialize** two pointers (`i` for children and `j` for cookies) starting at index 0.
4. **Compare** the current cookie with the current child's greed; if the cookie satisfies the child's greed, increment `i` to assign the cookie, and always move `j` to check the next cookie.
5. **Print** the total number of children satisfied (`i`) and **stop** the program.  

## Program:
```
/*
Program to assign cookies using greedy algorithm

Developed by: DHARSHINI K
Register Number: 212223230047

import java.util.*;

public class AssignCookies {
    
    public static int findContentChildren(int[] g, int[] s) {
        Arrays.sort(g);
        Arrays.sort(s);
        int i = 0, j = 0;
        while (i < g.length && j < s.length) {
            if (s[j] >= g[i]) i++;
            j++;
        }
        return i;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] g = new int[n];
        for (int i = 0; i < n; i++) g[i] = sc.nextInt();
        int m = sc.nextInt();
        int[] s = new int[m];
        for (int i = 0; i < m; i++) s[i] = sc.nextInt();
        System.out.println(findContentChildren(g, s));
    }
}
```

## Output:
<img width="395" height="346" alt="image" src="https://github.com/user-attachments/assets/aace18d6-4718-4eed-8473-f33560c43d2e" />

## Result:
The program was successfully implemented and the expected output is verified. 
