# Solution 1 - Semaphore
### Code

```java
class Foo {
    private Semaphore run2 = new Semaphore(0);
    private Semaphore run3 = new Semaphore(0);

    public void first(Runnable printFirst) throws InterruptedException {
        printFirst.run();
        run2.release();
    }

    public void second(Runnable printSecond) throws InterruptedException {
        run2.acquire();
        printSecond.run();
        run3.release();
    }

    public void third(Runnable printThird) throws InterruptedException {
        run3.acquire();
        printThird.run();
    }
}
```

### Time/Space Complexity

-  Time Complexity: O(1)
- Space Complexity: O(1)


# Solution 2 - CountDownLatch

Use a [CountDownLatch](https://docs.oracle.com/javase/7/docs/api/java/util/concurrent/CountDownLatch.html)

### Code

```java
class Foo {
    private CountDownLatch latch2 = new CountDownLatch(1);
    private CountDownLatch latch3 = new CountDownLatch(1);

    public void first(Runnable printFirst) throws InterruptedException {
        printFirst.run();
        latch2.countDown();
    }

    public void second(Runnable printSecond) throws InterruptedException {
        latch2.await();
        printSecond.run();
        latch3.countDown();
    }

    public void third(Runnable printThird) throws InterruptedException {
        latch3.await();
        printThird.run();
    }
}
```

### Time/Space Complexity

-  Time Complexity: O(1)
- Space Complexity: O(1)
