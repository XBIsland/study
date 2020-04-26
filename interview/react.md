# HOC、Render props、Hooks

- render props
  解决横切关注点（Cross Cutting Concern）：注意与pure component一起要小心使用；

  缺点：无法在 return 语句外访问数据，地狱嵌套

- HOC

  优点：不会影响内层组件的状态, 降低了耦合度

  缺点：props值可能被覆盖，数据来源追溯

- hook
  不会嵌套、可重命名、数据来源、return之外的也能用；



# Diff

##  react diff 原理, 如何从 O(n^3) 变成 O(n)，为什么要使用 key , 有什么好处?

- 一般来说，树的操作有，替换，删除，插入；两两对比两棵树的时间复杂度为O(n^2)+差异最小的转换方法O(n)  = O(n^3)

- 标准的diff算法是O(n^3)，要去除掉O(n^2)要从两两方面输入：
  1. 相同组件会产生相同的DOM结构，不同的组件则直接删除重新创建；
  2. 对于同一层的字节点，通过ID来区分他们；
- 12345 -> 123645 的时候不实用key的话，当发生位置变化的时候，会有大量的dom操作；
  1->1,2->2,3->3,6->4,4->5 再新增一个5；（`->`代表替换）而使用key的情况下，diff会把他们直接替换位置；

