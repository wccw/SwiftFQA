在Swift中，struct不仅可以定义成员变量，也可以定义成员方法，可以把结构体看成一个轻量级的类。

struct作为模型的优点：
* 安全性，struct为值类型，没有引用计数
* 内存，没有引用计数，不会造成内存泄露
* 速度，分配在栈中，速度比class快
* 线程安全，值类型是线程安全的

struct作为模型的缺点：
* 不能继承
* 不能被序列化为NSData对象
* OC无法调用Swift中的struct

如模型较小，无需继承，无需序列化存储，无需OC调用，建议使用struct

struct和class的异同点：
* struct不能继承，class可以继承
* struct分配在栈中，class分配在堆中，栈是编译时分配，堆是运行时分配
* struct可以直接在构造函数中初始化，class不可以
```
class CNode {
var data: String?
}

let cnode = CNode()
cnode.data = "cnode"


struct SNode {
var data: String?
}

let snode = SNode(data: "snode")

print(cnode.data!)   //cnode
print(snode.data!)   //snode
```
* struct为值类型，浅拷贝，class为指针类型，深拷贝
```
let cnode1: CNode = cnode
cnode1.data = "cnode1"

print(cnode.data!)   //cnode1
print(cnode1.data!)  //cnode1

var snode1 = snode
snode1.data = "snode1"

print(snode.data!)   //snode
print(snode1.data!)  //snode1
```
* struct在函数中修改属性，需要加上mutating，class不需要
```
extension CNode {
func modifyData(newData: String) {
self.data = newData
}
}

extension SNode {
mutating func modifyData(newData: String) {
self.data = newData
}
}
```



