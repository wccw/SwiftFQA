链式编程是将多个操作通过(.)链接在一起，使代码更加简洁，核心是返回本身
```
var name: String = ""

override func viewDidLoad() {
super.viewDidLoad()

class CalculateMaker {
var result: CGFloat = 0

func add(_ num: CGFloat) -> CalculateMaker {
result += num
return self
}

func sub(_ num: CGFloat) -> CalculateMaker {
result -= num
return self
}
}

var cal = CalculateMaker()
cal = cal.add(5).add(8).sub(3)
print(cal.result)

class Calculate {
static func start(calculateBlock:(CalculateMaker) -> ()) -> CGFloat {
let calculate = CalculateMaker()
calculateBlock(calculate)
return calculate.result
}
}

let result = Calculate.start { (calculate) in
calculate.add(1).add(4).add(4).add(2)
}
print(result)
```
