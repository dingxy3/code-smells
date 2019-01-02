

​                                                  **Extract Interface**

###### Problem

```
多个客户端代码使用类接口相同部分，另一个例子是：接口的某个部分被用
在2个类的相同部分
```

```
Employee

getRate()
hasSpecialSkill()
getName()
getDepartment()
```

###### Solution

```
移动相同的部分到它的接口里
```

```
<<interface>>
Billable

getRate()
hasSpecialSkill()
```

```
Employee

getRate()
hasSpecialSkill()
getName()
getDepartment()
```

###### 为什么重构

```
1、当类在不同情况下扮演不同角色，接口是非常合适的。使用Extract Interface
显示的指定是哪个角色
2、另一个明显的例子是当你需要描述一个类在它的服务器上执行的操作。如果最终计划使用不同
类别的服务器，所有的服务必须实现接口。
```



