### 乐观锁与悲观锁

* **悲观锁**

  如果有操作在拿取数据时，总会认为别人会修改，所以每次都会上锁，这样使得资源只能有一个线程使用，这个线程使用完以后，把锁交给下个线程，下个线程使用。

  数据库中的行锁，表锁，读写锁都是体现。

  synchronized和ReentrantLock等独占锁就是悲观锁思想的实现。

* **乐观锁**

  总是认为别人在使用的时候不会修改，所以不会对数据进行上锁，但在需要更新时，需要判断数据的及时性，可以使用版本号与CAS算法实现，它的使用场景是：多读的应用类型，可以提高吞吐量；

* **乐观锁实现的2种方式**

  - 版本号

    在数据表中加上一个版本的字段，来表示已经修改的次数，在每次需要修改数据的时候，版本号加1，在提交更新时，如果读取到的版本号与数据库中的版本号相同才会去提交；

  - CAS（比较交换算法）

    - 3个操作数：内存中V，旧预期值A，修改新值B


    - **当且仅当A==V时，把V的值替换为B**，其中比较与替换是一个原子操作；

* **乐观锁的问题**

  - ABA问题

    数据存在从a-b-a的修改，所以不能认为数据没有被修改过，jdk1.5以后，会检查当前的引用是否等于预期的引用，以及当前标志是否等于预期标志，全部相同才会替换；

  - 自旋锁问题

    如果没有成功就会一直循环知道成功为止，但是这样会消耗大量的CPU资源，

* CAS与synchronize使用情景比较

  如果是读>写，那么使用CAS比较高效，在写>读，使用synchronize;