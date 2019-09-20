属性分类：
* 存储属性：类、结构体
* 计算属性：类、结构体、枚举

### 存储属性
存储属性存储常量或变量

```
struct Person {
    var name: String
    let gender: Int
}

var person = Person(name: "roy", gender: 1)
person.name = "tom"
```

```
struct Person {
    var name: String
    let gender: Int
}

let person = Person(name: "roy", gender: 1)
//报错，let声明，不可修改值，因为结构体是值类型，let声明所有属性也被标记为常量
person.name = "tom"
```

### 计算属性
不直接存储值，而是通过get、set方法来取值或赋值
```
class Person {
    var firstName: String = ""
    var lastName: String = ""

    var fullName: String {
        get {
            return firstName + lastName
         }

        set {
            self.firstName = newValue.components(separatedBy: " ")[0]
            self.lastName = newValue.components(separatedBy: " ")[1]
        }
    }
}
let person = Person()
person.fullName = "wang fei"
print(person.fullName) //wangfei
```
只读属性
```
class Person {
    var firstName: String = ""
    var lastName: String = ""

    var fullName: String {
        get {
            return firstName + lastName
        }
    }
}
let person = Person()
person.firstName = "wang"
person.lastName = "fei"
print(person.fullName) //wangfei
```

### 属性监听
* willSet 在新的值被设置之前调用
* didSet 在新的值被设置之后调用
```
class Person {
var name: String = "" {
    willSet(newName) {
      print("new value:\(newName)")
   }

   didSet {
      print("old value:\(oldValue)")
    }
  }
}

let person = Person()
person.name = "wangfei"
person.name = "zhangfei"
```

```
new value:wangfei
old value:
new value:zhangfei
old value:wangfei
```

### 类型属性
```
class Person {
  static var personAge: Int = 100
}

print(Person.personAge)
```

### 懒加载属性
懒加载存储属性，被调用的时候才会初始化属性，在属性声明前用lazy表示懒加载存储属性
```
class DataImporter {
    var filename = "data.txt"
}

class DataManager {
    lazy var importer = DataImporter()
    var data = [String]()
}

//DataImporter未被创建
let manager = DataManager()
//DataImporter被创建
print(manager.importer.filename)
```

