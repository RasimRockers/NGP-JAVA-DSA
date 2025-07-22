
# Multithreading in Java

**Multithreading** is a process of executing multiple threads simultaneously. It helps perform **multiple tasks in parallel**, improving performance, especially in programs that are I/O-bound or have multiple independent tasks.

---

## 🔄 Thread Lifecycle in Java

| **State**       | **Description**                                                                 |
| --------------- | ------------------------------------------------------------------------------- |
| New             | Thread is created but not started (`new Thread()`).                             |
| Runnable        | Thread is ready to run but waiting for CPU (`start()`).                         |
| Running         | Thread is currently executing (`run()` method executing).                       |
| Blocked/Waiting | Thread is waiting for resources, lock, or another thread.                       |
| Timed Waiting   | Thread is sleeping or waiting for a specific time (`sleep()`, `join()`).        |
| Terminated      | Thread has finished execution or stopped manually (`stop()` or end of `run()`). |

---

## 🛠️ Key Thread Methods

| **Method**      | **Purpose**                           |
| --------------- | ------------------------------------- |
| `start()`       | Starts a new thread.                  |
| `run()`         | Contains the task logic.              |
| `sleep(ms)`     | Pauses thread for given milliseconds. |
| `join()`        | Waits for another thread to finish.   |
| `stop()`        | (Deprecated) Forces thread to stop.   |
| `isAlive()`     | Checks if thread is still running.    |
| `setPriority()` | Sets thread's priority.               |

---

## 👨‍💻 Two Ways to Create a Thread in Java

### 1. **By Extending Thread Class**

```java
class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running: " + Thread.currentThread().getName());
    }
}

public class TestThread {
    public static void main(String[] args) {
        MyThread t1 = new MyThread();
        t1.start(); // moves to Runnable -> Running
    }
}
```

---

### 2. **By Implementing Runnable Interface**

```java
class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Runnable thread: " + Thread.currentThread().getName());
    }
}

public class TestRunnable {
    public static void main(String[] args) {
        Thread t1 = new Thread(new MyRunnable());
        t1.start();
    }
}
```

---

## 🔁 Full Example Covering All Methods and States

```java
class WorkerThread extends Thread {
    public void run() {
        System.out.println("Running: " + Thread.currentThread().getName());
        try {
            Thread.sleep(2000);  // Moves to Timed Waiting
        } catch (InterruptedException e) {
            System.out.println("Interrupted");
        }
        System.out.println("Finished: " + Thread.currentThread().getName());
    }
}

public class ThreadLifecycleDemo {
    public static void main(String[] args) throws InterruptedException {
        WorkerThread t1 = new WorkerThread();
        WorkerThread t2 = new WorkerThread();

        System.out.println("State before start: " + t1.getState()); // NEW
        t1.start();
        t2.start();

        System.out.println("State after start: " + t1.getState()); // RUNNABLE

        t1.join();  // Main thread waits for t1 to finish
        t2.join();

        System.out.println("State after join: " + t1.getState()); // TERMINATED
    }
}
```

---

## 🎯 Role-Based Real-World Example: Online Food Ordering App

| **Thread**       | **Role**                    |
| ---------------- | --------------------------- |
| `OrderThread`    | Takes user’s order.         |
| `PaymentThread`  | Handles payment process.    |
| `CookingThread`  | Simulates food preparation. |
| `DeliveryThread` | Simulates delivery process. |

```java
class OrderThread extends Thread {
    public void run() {
        System.out.println("Order placed by customer.");
    }
}

class PaymentThread extends Thread {
    public void run() {
        System.out.println("Payment processing...");
    }
}

class CookingThread extends Thread {
    public void run() {
        System.out.println("Cooking food...");
    }
}

class DeliveryThread extends Thread {
    public void run() {
        System.out.println("Delivering order...");
    }
}

public class FoodApp {
    public static void main(String[] args) throws InterruptedException {
        OrderThread order = new OrderThread();
        PaymentThread payment = new PaymentThread();
        CookingThread cooking = new CookingThread();
        DeliveryThread delivery = new DeliveryThread();

        order.start();
        order.join(); // Wait until order is placed

        payment.start();
        payment.join(); // Wait until payment is complete

        cooking.start();
        cooking.join(); // Wait until food is cooked

        delivery.start();
    }
}
```

---


* Threads run concurrently and improve performance.
* Java supports threads via `Thread` class and `Runnable` interface.
* Lifecycle: New → Runnable → Running → Waiting → Terminated.
* Use `start()` to begin thread execution.
* Use `sleep()` to pause and `join()` to wait for another thread.

---

