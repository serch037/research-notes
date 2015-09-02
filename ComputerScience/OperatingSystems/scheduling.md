# Scheduling Notes

## Practice

### Chapter 7 
* Multiple threads, scheduling polcicy determines which runs
* Order of arrival is sub-optimal

#### Uniprocessor
* Basic policies: FIFO,Short First, Round Robin
* Compute-Bound vs. I/0 bound 
* Avoid idle times
* FIFO
    * Less overhead = More throughput
    * Suboptimal for short tasks
* SJF
    * Non-practical
    * Average response time--
    * Remaining time 
    * Bad variance in ART
    * Starvation and context switches
* RR
    * Taking turns, interrupt timer 
    * No starvation 
    * FIFO + SJF
    * Time quantum/slice
* Mix/Max
    * Assign until no resources left
    * Redistributes 
    * Priority queue = CPU expense 
* Multi-level Feedback 
    *  RR extension with ++ queues 
    * Priority preempts, equal, RR. 
    * Favor short tasks 
    * Time quantum, when used, drop level 
    * Tasks may yield (waitinf for I/O), and stay on level
    * Levels with different priorities 
    * Fairness: Monitor resources recieved per task
    * Two queues per level
        * Only scheduled if all fair shares run out 
        * If fair not recieved, up a level and viceversa
        * Priority is adjustable

#### Multiprocessor


#### Citations 
*  With the million-fold improvement in processor performance over the past thirty years, it might seem that we are a million times less likely to have anything waiting for its turn on the processor. We disagree! Server operating systems in particular are often overloaded. Parallel applications can create more work than processors, and if care isn’t taken in the design of the scheduling policy, performance can badly degrade. There are subtle relationships between scheduling policy and energy management on battery-powered devices such as smartphones and laptops. These questions apply whether the source of contention is the processor, memory, disk, or network, and so we will revisit them throughout the rest of this book.
(292)

* Keywords: 
    • Task. A user request. A task, sometimes called a job, can be any size, from skat-
ing the mouse across the screen to computing the shape of a newly discovered
protein. When discussing scheduling, we use the term task, rather than thread or
process, because a single thread may be responsible for multiple user requests,
e.g., in a word processor, each character typed is an individual user request to add that character to the file and display the result on the screen.
    • Response time (or delay). The user-perceived time to do some task.
    • Predictability. Low variance in response times for repeated requests.
    • Throughput. The rate at which tasks are completed.
    • Scheduling overhead. The time to switch from one task to another.
    • Fairness. Equality in the number and timeliness of resources given to each task.
    • Starvation. The lack of progress for one task, due to resources given to a higher priority task.
    * Workload: Set of tasks to perform, when they arrive and time to complete. Input to scheduling output
    * Work-conserving: Never leaves processor idle if there is work
    * Preemption: Ability to interrupt and switch tasks
    * Max/Min Fairness: iteratively maximises the minimum allocation of processess until all resources are asigned. 

    MFQ GOALS:
        • Responsiveness. Run short tasks quickly, as in SJF.
    • Low Overhead. Minimize the number of preemptions, as in FIFO, and minimize the time spent making scheduling decisions.
    • Starvation-Freedom. All tasks should make progress, as in Round Robin.
    • Background Tasks. Defer system maintenance tasks, such as disk defragmentation, so they do not interfere with user work.
    • Fairness. Assign (non-background) processes approximately their maxmin fair share of the processor.
