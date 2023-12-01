# Go语言基础

## 数据类型

- **布尔型**：布尔型的值只可以是常量 true 或者 false。一个简单的例子：var b bool = true。
- **数字类型**：整型 int 和浮点型 float32、float64，Go 语言支持整型和浮点型数字，并且支持复数，其中位的运算采用补码。
- **字符串类型:**字符串就是一串固定长度的字符连接起来的字符序列。Go 的字符串是由单个字节连接起来的。Go 语言的字符串的字节使用 UTF-8 编码标识 Unicode 文本。
- **派生类型:**包括：
  - (a) 指针类型（Pointer）
  - (b) 数组类型
  - (c) 结构化类型(struct)
  - (d) Channel 类型
  - (e) 函数类型
  - (f) 切片类型
  - (g) 接口类型（interface）
  - (h) Map 类型

**数字类型**，有unit8,unit16,unit32,unit64,int8,int16,int32,int64

**浮点型**：float32, float64

**其他类型**：byte（类似于uint8），rune（类似于int32），int和uint（一样大），uintptr（无符号整型，用于存放一个指针）

## 语言变量

Go语言变量由字母、数字、下划线组成，其中首个字符不能为数字。

声明变量的一般形式是使用`var`关键字：

```Go
var identifier type, identifier type
```

没有初始化，则变量默认值为零。

