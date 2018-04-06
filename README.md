# 计组实验（16340244 伍宇阳）  
#### 分别用 Java、C、MIPS 汇编以及 x86 汇编写一简单程序，比较各自目标代码的大小 
* Java
```sh
public class HelloWorld {
	public static void main(String[] args) {	
		System.out.println("hello world");
	}
}
```
* 运行结果  
[![N|Solid](http://imglf6.nosdn.127.net/img/aHBnT05NNXVUK2hidDI1U1REdm9iQW1kL3VGaEJWUXNicXplaHAvZlJXejRiN2RDTVU5MmF3PT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)  

* C
```sh
#include <stdio.h> 
int main(){
	printf("hello world");
    return 0;
} 
```
* 运行结果  
[![N|Solid](http://imglf4.nosdn.127.net/img/aHBnT05NNXVUK2hidDI1U1REdm9iSVJlN0NrN0ZaOXRKak1RRkc4WVJUTTl2RVl4ZFFjY1d3PT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

* MIPS
```sh
.text # 代码段声明
.globl main # 指明程序的入口地址main
main: # 入口地址main
    la $a0,str # 取字符串地址
    li $v0,4 # 4号功能调用，输出字符串
    syscall # 系统调用，输出字符串
    li $v0,10 # 退出
    syscall # 系统调用

.data # 数据段声明
    str: # 变量名称
        .asciiz "hello world\n" # 字符串定义
```
* 运行结果  
[![N|Solid](http://imglf6.nosdn.127.net/img/aHBnT05NNXVUK2hidDI1U1REdm9iSFZjbEc1enhrVkw2SlFDeHhsekNFdTlwUnpDbElxMWhRPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)

* x86
```sh
;完整段的Hello World程序
DATAS  SEGMENT
     STRING  DB  'Hello World',13,10,'$'
DATAS  ENDS

CODES  SEGMENT
     ASSUME    CS:CODES,DS:DATAS
START:
     MOV  AX,DATAS
     MOV  DS,AX
     LEA  DX,STRING
     MOV  AH,9
     INT  21H
   
     MOV  AH,4CH
     INT  21H
CODES  ENDS
    END   START

```
* 运行结果  
[![N|Solid](http://imglf3.nosdn.127.net/img/aHBnT05NNXVUK2hidDI1U1REdm9iQm1KdVBxc3pmSFV4ZVRaUkFiaElJdnZ6UFlicGU5N2hBPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)   


#### 总结 
> 综上，C 和 Java 的代码大小较小，MIPS 和 x86 的代码较多    


