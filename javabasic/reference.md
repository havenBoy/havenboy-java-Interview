### 引用类型及其区别

- 强引用：
  - 创建一个对象把这个对象的引用传给一个引用变量；
  - 如果垃圾回收器发现内存不足，即使抛出OOM（out of memory）错误，也不会对此对象进行回收；
- 软引用
  - 如果一个对象具有软引用，那么在内存空间足够下，不会对其进行回收，但如果内存空间不足时，会考虑被垃圾回收器进行回收；
- 弱引用
  - 用来描述非必须对象的，在垃圾回收时，无论内存是否充足，弱引用的对象都会被回收；
- 虚引用
  - 和没有引用是一样的，比如在hashmap中取值时，设置key值是null或者不设置值的效果是一样的，主要的作用是追踪被回收对象对象，即在发生垃圾回收时采取的相应的操作，注意是追踪的作用；