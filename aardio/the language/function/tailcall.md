# 尾调用

aardio所有文档请严格按本页示范的格式、HTML样式编写。

## 尾调用

请看下面的例子：

``` aau
function f (x){
         return f2(x) //调用另外一个函数以后不再做任何事称为尾调用
}
```

如果一个函数在调用另外一个函数以后不再做任何事称为尾调用。
尾调用不会返回原来的函数，所以不需要额外的栈保留调用函数的数据。

正确的尾调用：

* 尾调用必须是在最后一个return语句中
* return语句后面不能使用其他表达式，例如 return g(x) + 1 不是尾调用
* 参数中可以使用表达式。

递归调用函数是很浪费资源的，但是如果使用尾调用就不再需要大量的压栈，
无论递归多少次都不会导致栈溢出。

下面是一个递归尾调用的示例：
![](../../icon/warning.gif) 注意：该示例运行时间较长，可能需要数分钟以上，请谨慎运行!

``` aau
递归 = function ( 计数 ){
   sleep(1)

	if (  计数 <= 0   )
		return  计数
	else
		return 递归(  计数-1 )   // 这是一个的尾调用

}

io.open();

//调用递归函数
//因为是尾调用不会导致栈溢出
io.print( 递归( 99999  )  )
```

如果我们把 return dg(a-1) 改成 return dg(a-1)+1就不再是尾调用了，你会看到内存不断的增加直到栈溢出。