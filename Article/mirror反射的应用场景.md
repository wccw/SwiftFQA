Swift中的反射是基于Mirror的Struct实现的，目前Swift的反射功能比较弱，只能获取类型，成员信息

目前提供的API只能获取到值，不能赋值，如果需要实现字典模型转换功能，可以使用内存赋值，参考 [HandyJSON](https://github.com/alibaba/HandyJSON)的实现

```
class personClass: NSObject {
var name: String = "roy"
var sex: String = "boy"
}

class StudentClass: personClass {
var grade: Int = 80
var age: Int?
}

func test(obj: StudentClass) {
let superMirror = Mirror.init(reflecting: obj).superclassMirror

for (name, value) in (superMirror?.children)! {
print("\(String(describing: name!)) : \(value)")
}

let mirror = Mirror.init(reflecting: obj)

for (name, value) in (mirror.children) {
print("\(String(describing: name!)) : \(value)")
}
}
```

```
Result:
name : roy
sex : boy
grade : 80
age : nil
```





