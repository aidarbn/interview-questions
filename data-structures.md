<details>
<summary>What is delay queue?</summary>

Delay queue is a special queue whose elements can only be consumed after the specified delay has arrived.Delayed queue implementation usually relies on a scheduled task, which regularly scan elements in the queue, move expired elements to another queue, from which consumers consume.

Sample code example:

```go
// chat gpt generated code
package main

import (
 "container/heap"
 "fmt"
 "time"
)

// Task represents a delayed task.
type Task struct {
 Name        string
 ScheduledAt time.Time
}

// TaskQueue is a priority queue for tasks.
type TaskQueue []*Task

// Len returns the length of the queue.
func (q TaskQueue) Len() int { return len(q) }

// Less compares tasks based on their scheduled times.
func (q TaskQueue) Less(i, j int) bool {
 return q[i].ScheduledAt.Before(q[j].ScheduledAt)
}

// Swap swaps the positions of two tasks in the queue.
func (q TaskQueue) Swap(i, j int) { q[i], q[j] = q[j], q[i] }

// Push adds a task to the queue.
func (q *TaskQueue) Push(x interface{}) {
 task := x.(*Task)
 *q = append(*q, task)
}

// Pop removes and returns the earliest task from the queue.
func (q *TaskQueue) Pop() interface{} {
 old := *q
 n := len(old)
 task := old[n-1]
 *q = old[0 : n-1]
 return task
}

// AddTask adds a task with a specified delay to the queue.
func (q *TaskQueue) AddTask(name string, delay time.Duration) {
 task := &Task{
  Name:        name,
  ScheduledAt: time.Now().Add(delay),
 }
 heap.Push(q, task)
}

// ProcessTasks processes tasks that are ready for execution.
func (q *TaskQueue) ProcessTasks() {
 currentTime := time.Now()

 for q.Len() > 0 {
  task := heap.Pop(q).(*Task)
  if currentTime.After(task.ScheduledAt) {
   fmt.Printf("Executing task: %s at %s\n", task.Name, currentTime.Format(time.RFC3339))
  } else {
   // Re-insert the task if not ready yet
   heap.Push(q, task)
   break
  }
 }
}

func main() {
 taskQueue := make(TaskQueue, 0)
 heap.Init(&taskQueue)

 // Add tasks with different delay periods
 taskQueue.AddTask("Task 1", 5*time.Second)
 taskQueue.AddTask("Task 2", 2*time.Second)
 taskQueue.AddTask("Task 3", 8*time.Second)

 // Simulate the passage of time
 time.Sleep(3 * time.Second)

 // Process tasks that are ready for execution
 taskQueue.ProcessTasks()
}
```

[https://go-zero.dev/en/docs/tasks/queue/delay-queue](https://go-zero.dev/en/docs/tasks/queue/delay-queue)
</details>

<details>
<summary>What is bloom filter?</summary>

A bloom filter is a probabilistic data structure that is based on hashing. It is extremely space efficient and is typically used to add elements to a set and test if an element is in a set. Though, the elements themselves are not added to a set. Instead a hash of the elements is added to the set.

When testing if an element is in the bloom filter, false positives are possible. It will either say that an element is definitely not in the set or that it is possible the element is in the set.

A bloom filter is very much like a hash table in that it will use a hash function to map a key to a bucket. However, it will not store that key in that bucket, it will simply mark it as filled. So, many keys might map to same filled bucket, creating false positives.

[https://brilliant.org/wiki/bloom-filter/#:~:text=A%20bloom%20filter%20is%20a,is%20added%20to%20the%20set.](https://brilliant.org/wiki/bloom-filter/#:~:text=A%20bloom%20filter%20is%20a,is%20added%20to%20the%20set.)
</details>
