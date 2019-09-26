KVC（Key-value coding）键值编码，允许开发者通过key间接访问对象的属性，或者给对象属性赋值，而不需要调用明确的存取方法。这样可以在运行时动态访问和修改属性，是iOS的黑魔法之一，底层使用isa-swizzing技术实现。

OC 中KVC是因为遵循了NSKeyValueCoding协议，在Swift中使用KVC，需要继承NSObject，并且需要在变量前面添加@objc

KVC常用场景：
* 1.动态取值和赋值 
* 2.用KVC访问和修改私有变量
* 3.字典模型转换
* 4.修改原生控件的一些属性，可以使用KVC修改，iOS13上会崩溃

```
class Weather: NSObject {
     @objc var time: String?
     @objc private var weather: String?
}
let wea = Weather()

//动态取值和赋值
wea.setValue("2019-10-1", forKeyPath: "time")

//字典转模型
let weatherJson = ["weather":"cloudy",
                  "time":"2019-10-1"]
wea.setValuesForKeys(weatherJson)
```

获取私有属性，并修改变量
```
var count: UInt32 = 0
let ivars = class_copyIvarList(Weather.self, &count)
for i in 0..<numericCast(count) {
  let name = ivar_getName((ivars?[i])!)
  print(String(cString: name!)) //time weather
}
wea.setValue("sunday", forKey: "weather")
 ```


