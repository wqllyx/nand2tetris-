# Nand2Tetris

与 、与非

或、或非

异或、 等价

x->y 、y->x



![image-20240709090904595](README.assets/image-20240709090904595.png)

![image-20240709090940465](README.assets/image-20240709090940465.png)

![image-20240709090644362](README.assets/image-20240709090644362.png)

## Project1 基本逻辑门

典型的计算机体系结构基于一组基本逻辑门，如 And、Or、Mux 等，以及它们的按位版本 And16、Or16、Mux16 等（假设是 16 位机器）。在这个项目中，您将构建一组典型的基本逻辑门。这些门构成了基本构建块，您将在以后的项目中构建计算机的 CPU 和 RAM 芯片。



### Nand

由于Nand被认为是原始的，所以没有必要实现它。

以Nand为基础元件，实现其他元件。

已经实现的元件可以用来实现别的元件。

**Nand门可以使用4个晶体管来实现：两个N型和两个P型。**

### Nor

Nor也被认为是原始的，所以没有必要实现它。

**Nor门可以使用4个晶体管来实现：两个N型和两个P型。**

### Not

**使用1个Nand实现Not**

```c
Not(x) = Nand(x,x)
```

- 因为Nand的其中两个逻辑，正好符合非门逻辑。输入同时为1时，输出为0。输入同时为0时，输出为1。

**最简单的非门不需要使用Nand实现。只需要使用两个晶体管即可实现**。![image-20240709084240311](README.assets/image-20240709084240311.png)

### And

**使用一个Nand和一个Not实现And**

```c
And(a,b) = Not( Nand(a,b) )
```

**因此与门的实现需要六个晶体管。（一个nand4个，一个not两个）**

![image-20240709085157751](README.assets/image-20240709085157751.png)

### Or

**使用三个非门和一个与门实现Or**

```bash
Or = Not( And( Not(a), Not(b) ) )
```



**实际上Or可以通过或非门和一个非门实现。需要6个晶体管。**

### Xor

需要两个非门，两个与门，一个或门

```c
Xor = OR( And(a, Not(b)), And(Not(a), b) )
```

### Mux

使用二值逻辑，从真值表获得Mux逻辑表达式。

```c
Mux = ab'c' + abc' + a'bc + abc
	= (ab' + ab) c' + (a'b + ab ) c
	= ac' + bc'
```



### DMux

DMux的特点：

```
If sel=0 then {a=in, b=0} else {a=0, b=in}.
```



- 当sel为1时，输出a一直为0.输出b = 输入 in
- 当sel为0时，输出a = 输入 in 。输出a 一直为0。

```c
Not(in= sel, out= notsel);
And(a= in, b=notsel , out= a);  // If sel=0 then {a=in, b=0}
And(a= in, b= sel, out= b); // else {a=0, b=in}
```

### Not16

每个输入的位数增加。输出位也增加。

但是有可能只有两个输入。

### And16
### Or16
### Mux16
### Or8Way

输入数量增加。每个输入的位有可能还是一位。或多位。输出是一位。

### Mux4Way16

**4路（4输入）16位的选择器。**

### Mux8Way16

### DMux4Way

### DMux8Way

#  参考

[NJU](http://ws.nju.edu.cn/courses/dm/courseware/20150504-Boolean_Algebra.pdf)
