​                                     **Extract Method**

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

```
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

