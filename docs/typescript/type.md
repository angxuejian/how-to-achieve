# 类型

1、any：没有任何限制，该类型的变量可以随意赋值。顶层类型(top type)

2、unknown：any类型的严格版，可以设置任何类型，除any和unknown类型外不能随意赋值和使用，必须**类型缩小**后才可以使用。顶层类型(top type)

3、never：空类型，不包含任何值，定义never类型后不可以赋任何值，常常用于死循环和抛出异常的函数。底层类型(bottom type)


在ts中，可以利用never类型的特性来实现详情的检查，示例如下：
```
type Foo = string | number;

function controlFlowAnalysisWithNever(foo: Foo) {
  if(typeof foo === "string") {
    // 这里 foo 被收窄为 string 类型
  } else if(typeof foo === "number") {
    // 这里 foo 被收窄为 number 类型
  } else {
    // foo 在这里是 never
    const check: never = foo;
  }
}
```
注意在else分支，我们把foo赋值给一个显示声明的never变量。如果逻辑一切正常，那这里就能够compile通过。假如后续有人修改了Foo的类型：
```
type Foo = string | number | boolean;
```
然而又忘记修改`controlFlowAnalysisWithNever`方法中的if判断，这时就会走进else分支，将boolean类型的值赋值给never类型的变量，这时就会无法赋值给never类型的变量，产生一个compile错误。通过这个方法，我们就可以确保`controlFlowAnalysisWithNever`方法不会出现未知的类型，**写出类型绝对安全的代码**

更详细的never类型的讲解可以看[这里](https://cloud.tencent.com/developer/article/1594872)