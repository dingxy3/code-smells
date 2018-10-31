####                                                 Bloaters(吸血者)

```
    bloaters是一种代码、方法、类已经发展到了一个巨大的规模，以至很难工作。通常这种情况不会立马产生，是经过时间的积累项目的发展，尤其是开发者没有努力的想要去改变根除它。
```

**Long Method **

症状：

```
一个方法包含了太多行数的代码，通常某个方法已经超过了10行并且开始促使你问为什么呢
```

问题原因：

```
   就像加州旅馆一样，一些东西总是被添加进去但是却没有任何东西被删除掉。因为写代码总是比读代码容易。这种习惯方法气味一直没有被注意到直到它变成了一个丑陋的超大的野兽。
   心理上，通常新建一个新方法难度超过了在先有方法上去添加改变：“但是它仅仅有2行，为了那个创建一个新的方法是没有用的”这就意味着另一个方法被添加了然后又是另一个，产生了一团混乱的意大利面条代码
```

治疗：

```
根据经验来说，如果你感觉到需要增加一些注释在一个方法内部，你就应该拿走这些代码把它放到一个新的方法里。如果它需要解释的话，甚至一个单独的行应该被分割成一个新的单独的方法。如果这个方法有一个清晰的名字，没有人为了知道这个方法干了什么会而查看这个代码内部的具体实现。
```

* 减少一个方法体的长度，使用 提取方法  Extract Method

  **Problem:**

  ```java
  /**
    *你有一个可以组织在一起的代码片段
    */
  void printOwing() {
    printBanner();
  
    //print details
    System.out.println("name: " + name);
    System.out.println("amount: " + getOutstanding());
  }
  ```

  **Solution:**

  ```java
  /**
   *移动这些代码到一个单独的新的方法，使用方法调用替换这些老的代码
   */ 
  void printOwing() {
    printBanner();
    printDetails(getOutstanding());
  }
  
  void printDetails(double outstanding) {
    System.out.println("name: " + name);
    System.out.println("amount: " + outstanding);
  }
  ```

  