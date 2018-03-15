## **容器类问题**



**1.边访问List，边删除?**

使用Iterator去实现。

**2.ArrayList底层是数组实现的，数组的长度是固定的，为什么ArrayList的长度可以是动态的？**

ArrayList内部的数据可以自动扩容

https://juejin.im/post/59dd70966fb9a0452845741e

**3.LinkedList和ArrayList的区别?**

Linked插入删除速度快，ArrayList随机访问速度快

**4.ArrayList和Vector的区别?**

ArrayList不是线程安全的，Vector是。

内部实现，Vector扩容1倍，ArrayList扩容0.5倍。

**5.HashTable和HashMap的区别?**

HashTable和HashMap类的作用一样，实际上，他们拥有相同的接口。HashTable方法是同步的，如果对同步性或遗留性代码没有任何要求，就应该使用HashMap。

