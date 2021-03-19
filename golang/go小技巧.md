```go
// 获取正在运行的函数名
func runFuncName() string {
	pc := make([]uintptr, 1)
	runtime.Callers(2, pc)
	f := runtime.FuncForPC(pc[0])
	return f.Name()
}
```



## **我如何保证我的类型满足某个接口？**

可以通过尝试赋值来要求编译器检查类型 T 是否实现了接口 I：

```go
type T struct{}

var _ I = T{}  // 确认T是否实现了I。
```

若 T 未实现 I，则错误会在编译时捕获。



## 高效读取文件

当读取小文件时，使用ioutil效率明显优于os和bufio，但如果是大文件，bufio读取会更快。

读取文件中一行内容时，ReadSlice和ReadLine性能优于ReadBytes和ReadString，但由于ReadLine对换行的处理更加全面（兼容\n和\r\n换行），因此，实际开发过程中，建议使用ReadLine函数。



## 高效拼接字符串

\+ 连接适用于短小的、常量字符串（明确的，非变量），因为编译器会给我们优化。

Join是比较统一的拼接，不太灵活

fmt和buffer基本上不推荐

builder从性能和灵活性上，都是上佳的选择， 字符串越多，性能优势更加明显。

通过Grow方法预先分配内存优化

```go
func StringBuilder(p []string,cap int) string { 
	var b strings.Builder 
	l:=len(p) 
	b.Grow(cap) 
	for i:=0;i<l;i++{ 
		b.WriteString(p[i]) 
	} 
	return b.String() 
}
```



## 获取当前可执行文件目录

```go
os.Chdir(filepath.Dir(os.Args[0])) 
```



## 存储大小常量定义

```go
const (
  _  = 1 << (10 * iota)
  KB // 1024
  MB // 1048576
  GB // 1073741824
  TB // ‭1099511627776‬
  PB // ‭1125899906842624‬
  EB // ‭1152921504606846976‬
  ZB // ‭1180591620717411303424‬
  YB // ‭1208925819614629174706176‬
)
```

ZB和YB都已经超出了uint64的表示范围



## 未知网页编码转utf8编码

![IMG_1041](https://cdn.jsdelivr.net/gh/lian-yang/images@master/images/IMG_1041.PNG)

## copy文件技巧

![0746](https://cdn.jsdelivr.net/gh/lian-yang/images@master/images/0746.PNG)



**如果要得到字符串的字符数，可使用 “unicode/utf8” 包中的 RuneCountInString(str string) (n int)**

**注意： RuneCountInString 并不总是返回我们看到的字符数，因为有的字符会占用 2 个 rune 如 é** 

**recover() 仅在 defer 执行的函数中调用才会生效。**

**对** **defer** **延迟执行的函数，它的参数会在声明时候就会求出具体值，而不是在执行时才求值**

