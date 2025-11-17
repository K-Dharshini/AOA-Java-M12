
# EX 2C Job Sequencing using Greedy Approach
## DATE:
## AIM:
To write a Java program to for given constraints. You're given N jobs, each with:

- A unique jobId
- A deadline (by which it must be completed)
- A profit (earned only if completed on or before the deadline)

Each job:
- Takes exactly 1 unit of time
- Only one job can be done at a time

Your goal is to maximize total profit while completing the maximum number of jobs possible within their deadlines.

## Algorithm
1. **Start** the program and read the number of jobs `n`, then input each job's `id`, `deadline`, and `profit` into a job array.
2. **Sort** all jobs in descending order based on profit so that higher-profit jobs are considered first.
3. **Find** the maximum deadline among all jobs and create a boolean array `slot[]` to track available time slots.
4. **Iterate** through each job and try to place it in the latest available slot on or before its deadline; if free, mark the slot and update the job count and total profit.
5. **Print** the total number of jobs done and the maximum profit obtained, then **stop** the program.   

## Program:
```
Program to implement job sequencing

Developed by: DHARSHINI K
Register Number: 212223230047

import java.util.*;

public class JobScheduling {

    static class Job {
        int id, deadline, profit;

        Job(int id, int deadline, int profit) {
            this.id = id;
            this.deadline = deadline;
            this.profit = profit;
        }
    }

    public static int[] jobScheduling(Job[] jobs, int n) {
        Arrays.sort(jobs, (a, b) -> b.profit - a.profit);

        int maxDeadline = 0;
        for (Job job : jobs) {
            maxDeadline = Math.max(maxDeadline, job.deadline);
        }

        boolean[] slot = new boolean[maxDeadline + 1];
        int jobsDone = 0, totalProfit = 0;

        for (Job job : jobs) {
            for (int j = job.deadline; j > 0; j--) {
                if (!slot[j]) {
                    slot[j] = true;
                    jobsDone++;
                    totalProfit += job.profit;
                    break;
                }
            }
        }

        return new int[]{jobsDone, totalProfit};
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt(); // Number of jobs
        Job[] jobs = new Job[n];

        for (int i = 0; i < n; i++) {
            int id = sc.nextInt();
            int deadline = sc.nextInt();
            int profit = sc.nextInt();
            jobs[i] = new Job(id, deadline, profit);
        }

        int[] result = jobScheduling(jobs, n);
        System.out.println(result[0] + " " + result[1]);
    }
}
```

## Output:
<img width="388" height="418" alt="image" src="https://github.com/user-attachments/assets/f9d76e7a-fbec-477a-8059-eb0e586d177b" />

## Result:
The program was successfully implemented and the expected output is verified.
