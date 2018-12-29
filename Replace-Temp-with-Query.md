# replace temp with query

**problem**

```
将表达式结果放在本地变量中，以便稍后在代码中使用
```

```java
double calculateTotal() {
  double basePrice = quantity * itemPrice;
  if (basePrice > 1000) {
    return basePrice * 0.95;
  }
  else {
    return basePrice * 0.98;
  }
}
```

**solution**

```
将整个表达式移动到一个单独的方法，并且从中返回结果，使用查询方法而不是变量，如果有需要，
将其他方法合并到新方法中
```

```java
double calculateTotal() {
  if (basePrice() > 1000) {
    return basePrice() * 0.95;
  }
  else {
    return basePrice() * 0.98;
  }
}
double basePrice() {
  return quantity * itemPrice;
}
```

**为什么重构**

```这种重构能为```[Extract Method](./Extractmethod.md)```打下基础相对于一个长方法的部分，```

```相同的表达式有时候也会被发现在其他的方法里使用，这也是考虑新建一个通用方法的原因```

**好处**

```
更加可读的代码。相较于这行代码 orderPrice() * 0.2 getTax()很容易明白这个方法的目的。
通过删除重复的代码使得代码更加轻盈，如果这行代码被在多个重复代码中使用。
```

**需要知道的事**

**性能**

```
 这种重构是不是会引起一个新的问题，是否会引起性能下降，最诚实的答案是：是的，
  这个结果代码会因为查询一个新方法而导致性能下降，
  但是相对于现在超快的cpu处理速度和卓越的编译器，这种负担几乎可以忽略不计，
  相比较而言，可读的代码和这个抽出的新方法可以用在程序的其他代码地方
  -谢谢这样的重构-有着非常明显的好处。
  尽管如此，如果你的临时变量被用来缓存耗时的表达式结果，你可能会停止重构直到提取这个表达式到一个新的方法里。
```

**怎么样重构**

```
 1、确保一个变量在一个方法里被赋值一次仅仅一次，如果不是，那么
  使用Split Temporary Variable来确保你的变量将会被仅仅用来存储
  你的表达式的结果。
  2、使用提取方法的方法将你感兴趣的表达式放在一个新方法里，确保
  这个方法仅仅是返回一个值，并不改变这个对象的状态，如果这个方法
  影响对象的可见状态，使用Separate Query from Modifier
  3、对于你的新方法用查询去替换你的变量
```

