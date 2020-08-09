关于HashMap的总结

1.HashMap是基于Map接口的实现，存储键值对时，它可以接收null的键值，
是非同步的，HashMap存储着Entry(hash, key, value, next)对象。
2.HashMap的工作原理
 通过hash的方法，通过put和get存储和获取对象。存储对象时，
 我们将K/V传给put方法时，它调用hashCode计算hash从而得到bucket位置，
 进一步存储，HashMap会根据当前bucket的占用情况自动调整容量(超过Load Facotr则resize为原来的2倍)。
 获取对象时，我们将K传给get，它调用hashCode计算hash从而得到bucket位置，并进一步调用equals()方法确定键值对。
 如果发生碰撞的时候，Hashmap通过链表将产生碰撞冲突的元素组织起来，在Java 8中，
 如果一个bucket中碰撞冲突的元素超过某个限制(默认是8)，
 则使用红黑树来替换链表，从而提高速度。
 3.通过对key的hashCode()进行hashing，并计算下标( n-1 & hash)，
 从而获得buckets的位置。如果产生碰撞，则利用key.equals()方法去链表或树中去查找对应的节点
 4.在Java 1.8的实现中，是通过hashCode()的高16位异或低16位实现的：
 (h = k.hashCode()) ^ (h >>> 16)，主要是从速度、功效、质量来考虑的，
 这么做可以在bucket的n比较小的时候，也能保证考虑到高低bit都参与到hash的计算中，
 同时不会有太大的开销。
 5.如果超过了负载因子(默认0.75)，则会重新resize一个原来长度两倍的HashMap，
 并且重新调用hash方法。