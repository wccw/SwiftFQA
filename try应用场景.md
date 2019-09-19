 try处理异常的三种方式：
 
 * try : 标准的处理方式, 该方式必须结合do catch来处理
 
 * try? :告诉系统可能有错, 也可能没错, 如果发生错误, 返回nil, 如果没有发生错误, 数据包装成一个可选类型的值返回
 
 * try! : 告诉系统一定没错, 如果发生错误, 程序会崩溃. 不推荐使用
  
  ```  
  let jsonObject = try! JSONSerialization.jsonObject(with: jsonArrayString.data(using: String.Encoding.utf8)!, options: .allowFragments)
  ```
  
  ```
  if let jsonObject = try? JSONSerialization.jsonObject(with: jsonArrayString.data(using: String.Encoding.utf8)!, options: .allowFragments) {
  
  }
  ```
  
  ```
  do {
      let jsonObject = try JSONSerialization.jsonObject(with: jsonArrayString.data(using: String.Encoding.utf8)!, options: .allowFragments)
      if let jsonDict = jsonObject as? [String: Any] {
      
      }
  } catch let error {
  
  }
  ```
```
