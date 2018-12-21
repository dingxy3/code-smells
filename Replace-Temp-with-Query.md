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

```

```

