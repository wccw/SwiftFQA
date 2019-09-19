try的使用原则

* try : 标准的处理方式, 该方式必须结合do catch来处理
 
* try? :告诉系统可能有错, 也可能没错, 如果发生错误, 那么返回nil, 如果没有发生错误, 数据包装成一个可选类型的值返回
 
* try! : 告诉系统一定没错, 如果发生错误, 程序会崩溃. 不推荐使用

代码示例：
  
```  
do {
    let jsonObject = try JSONSerialization.jsonObject(with: jsonArrayString.data(using: String.Encoding.utf8)!, options: .allowFragments)
 
} catch let error {

}

if let jsonObject = try? JSONSerialization.jsonObject(with: jsonArrayString.data(using: String.Encoding.utf8)!, options: .allowFragments) {

}

let jsonObject = try! JSONSerialization.jsonObject(with: jsonArrayString.data(using: String.Encoding.utf8)!, options: .allowFragments)
  
```
