<p style = "font-size: 30px;"> AI Summary:</p>

**Presentation 1: Process Scheduling** 

**Key Topics:**

1. **Why Scheduling is Important**:

• Single CPU systems need scheduling to avoid idle CPU time during I/O operations.

• Multiprogramming increases CPU utilization by overlapping CPU-bound and I/O-bound processes.

2. **Types of Scheduling**:

• **Long-Term (Admission Scheduler)**: Decides if a new job can be added based on system resources.

• **Medium-Term (Memory Scheduler)**: Manages memory allocation, swapping processes between disk and memory to prevent thrashing.

• **Short-Term (CPU Scheduler)**: Decides which process runs next, focusing on speed and efficiency.

3. **OS Types and Scheduling Goals**:

• **Batch Systems**: Maximize throughput and CPU utilization, minimize turnaround time.

• **Interactive Systems**: Focus on fast response time.

• **Real-Time Systems**: Meet strict deadlines with predictable scheduling.

  

**Presentation 2: Batch and Non-Preemptive Scheduling** 

**Key Topics:**

1. **Batch Scheduling**:

• Goal is to maximize CPU utilization and minimize turnaround time.

• Can use priority-based scheduling, and can be preemptive or non-preemptive.

2. **Non-Preemptive Algorithms**:

• **First-Come-First-Serve (FCFS)**: Simple but can lead to long waiting times.

• **Shortest Job First (SJF)**: Optimal if job durations are known, leads to lower mean turnaround time.

• **Priority Scheduling**: Jobs are assigned priorities, with higher-priority jobs running first.

3. **Turnaround Time Calculation**:

• Turnaround time = Finish time - Arrival time.

• Mean Turnaround Time (MTT) is the average of all jobs’ turnaround times, used to compare scheduling efficiency.

  

**Presentation 3: Preemptive and Real-Time Scheduling** 

**Key Topics:**

1. **Preemptive Scheduling**:

• Allows interruption of a running process to switch to another, improving responsiveness.

• **Algorithms**:

• **Shortest Remaining Time First (SRTF)**: Chooses the job with the least time remaining, optimal but context switches can increase overhead.

• **Round Robin (RR)**: Jobs are cycled with fixed quantum times, balancing fairness and responsiveness.

• **Preemptive Priority**: The highest priority job runs first, often used with round-robin for time-sharing systems.

2. **Real-Time Scheduling**:

• **Static Scheduling**: Priorities are fixed, suitable for systems with strict deadlines (e.g., flight controls).

• **Dynamic Scheduling**: Prioritizes jobs based on deadlines, adjusting priorities as needed (e.g., multimedia streaming).
