inout参数使用&，容易和C和C++中混淆，误以为是传递引用，实际情况是通过值传递，然后复制回来，传入的值不能用let修饰

inout参数将一个值传递给函数，函数可以改变这个值，然后将原来的值替换，从函数中传出

//Demo1
var num = 50

func increment(_ value: inout Int) {
value += 50
}

increment(&num)
print(num)  //100


//Demo2
var num1 = 10, num2 = 20

func swapInoutNumber(_ num1: inout Int, _ numb2: inout Int) {
let temp = num1
num1 = numb2
numb2 = temp
}

swapInoutNumber(&num1, &num2)
print(num1, num2)  //20 10
