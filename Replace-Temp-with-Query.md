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

```相同的表达式有时候也会被发现在其他的方法里，这也是考虑新建一个通用方法的原因```

**好处**

```
更加可读的代码。相较于这行代码 orderPrice() * 0.2 getTax()很容易明白这个方法的目的。
通过删除重复的代码使得代码更加轻盈，如果这行代码被在多个重复代码中使用。
```

**需要知道的事**

**Performance**

```

```

