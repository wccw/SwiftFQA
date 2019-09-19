Guard是Swift 2推出的判断语句，相较于if，优点如下：
* guard把不符合条件的事件前置，类似于保镖，在坏事情进门之前把它们踢出去
* 减少嵌套层次，代码间接易读

```
func doSomething(str: String?) {
guard let _str = str else {
return
}
//do something
}

func doSomething(str: String?) {
if let _str = str {
//do something
}
}
```
