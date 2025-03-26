The **Job Sequencing Problem** is a classic optimization problem where the goal is to schedule jobs on a single machine to maximize the profit, given deadlines and profits for each job. The optimal solution can be achieved using a **Greedy Algorithm**.

**Problem Statement:** You are given a set of N jobs where each job comes with a **deadline** and **profit**. The profit can only be earned upon completing the job within its deadline. Find the **number of jobs** done and the **maximum profit** that can be obtained. Each job takes a **single unit** of time and only **one job** can be performed at a time.

**Example 1:**

**Input:** N = 4, Jobs = {(1,4,20),(2,1,10),(3,1,40),(4,1,30)}

**Output**: 2 60

**Explanation:** The 3rd job with a deadline 1 is performed during the first unit of time .The 1st job is performed during the second unit of time as its deadline is 4.
Profit = 40 + 20 = 60

**Example 2:**

**Input:** N = 5, Jobs = {(1,2,100),(2,1,19),(3,2,27),(4,1,25),(5,1,15)}

**Output:** 2 127

**Explanation:** The  first and third job both having a deadline 2 give the highest profit. 
Profit = 100 + 27 = 127

---

### **Approach**:

1. **Sort Jobs by Profit**:
    - Sort all jobs in decreasing order of profit, since maximizing profit is the objective.
2. **Assign Jobs Greedily**:
    - Iterate through the sorted jobs and assign each job to the latest available slot before its deadline.
    - Use a data structure (like an array) to track occupied time slots.
3. **Check Feasibility**:
    - Only assign jobs to free slots within their deadlines.

---

### **JavaScript Implementation**:

```javascript
function jobSequencing(jobs, maxDeadline) {
    // Sort jobs by profit in descending order
    jobs.sort((a, b) => b.profit - a.profit);

    const result = new Array(maxDeadline).fill(false); // Time slots
    const jobOrder = new Array(maxDeadline).fill(null); // Track jobs selected
    let totalProfit = 0;

    for (let job of jobs) {
        // Find a free slot for the job (starting from the last possible slot)
        for (let slot = Math.min(job.deadline, maxDeadline) - 1; slot >= 0; slot--) {
            if (!result[slot]) {
                result[slot] = true; // Mark this slot as filled
                jobOrder[slot] = job.id; // Record the job
                totalProfit += job.profit; // Add profit
                break;
            }
        }
    }

    return { jobOrder: jobOrder.filter(job => job !== null), totalProfit };
}

// Example usage:
const jobs = [
    { id: "Job1", deadline: 2, profit: 100 },
    { id: "Job2", deadline: 1, profit: 19 },
    { id: "Job3", deadline: 2, profit: 27 },
    { id: "Job4", deadline: 1, profit: 25 },
    { id: "Job5", deadline: 3, profit: 15 }
];

const maxDeadline = 3; // Max deadline for jobs
const result = jobSequencing(jobs, maxDeadline);

console.log("Job Order:", result.jobOrder);
console.log("Total Profit:", result.totalProfit);
```

---

### **Explanation**:

1. **Input**:
    - Each job has an `id`, a `deadline` (latest time the job can be completed), and a `profit`.
    - `jobs` is an array of such job objects.
2. **Sorting**:
    - Jobs are sorted by their profit in descending order to prioritize high-profit jobs.
3. **Assign Slots**:
    - For each job, find the latest available time slot that is before or equal to its deadline and assign the job there.
    - Update total profit and mark the slot as occupied.
4. **Output**:
    - The `jobOrder` gives the sequence of jobs selected, and `totalProfit` is the sum of profits from the selected jobs.

---

### **Example**:

For `jobs = [Job1, Job2, Job3, Job4, Job5]` with:

- Profits = [100, 19, 27, 25, 15]
    
- Deadlines = [2, 1, 2, 1, 3]
    
- After sorting: `[Job1, Job3, Job4, Job2, Job5]`
    
- Selected Jobs: `Job1 -> Job3 -> Job5`
    
- Total Profit: `100 + 27 + 15 = 142`
    

---

### **Time Complexity**:

- **Sorting Jobs**: O(n log n), where `n` is the number of jobs.
- **Assigning Slots**: O(n × m), where `m` is the maximum deadline.
- Total: **O(n log n + n × m)**.

---

This is an optimal and practical solution for the Job Sequencing Problem using the greedy approach. Let me know if you'd like further clarification or help!
