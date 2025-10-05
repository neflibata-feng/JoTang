---
title: Task0
date: 2025-10-05 10:09:38
tags:
categories: JoTang2025
---

> [!NOTE]
>
> 我之前用eclipse写Java比较多，涉及Java的东西跟IDEA没什么区别哈（就是文件组织eclipse更严格些，比如要求你一定要打包），区别大的是插件不一样（毕竟eclipse开源嘛），我用惯了就不换IDEA了啊😁。

> [!NOTE]
>
> 还有我9月份开始换成JDK25了，最新的长期支持版本，跟21有3个比较大的区别要说明一下。
>
> 1.主方法的写法有变化
>
> ​     旧写法
>
> ```java
> public static void main(String args[]){
>     
> }
> ```
>
> ​    新的写法
>
> ```java
> void main(){
> 
> }
> ```
>
> 2.导包的方式有变化，以GUI为例
>
> ​    旧的写法
>
> ```java
> import java.awt;
> ```
>
> ​    新的写法要求在模块化文件里添加以下代码
>
>  
>
> ```java
> requires java.desktop;
> ```
>
> ​    唯一的好处在于可以导入同一模块的所有包，不用一个一个导入，其实我觉得这样会很混乱
>
> 3.this 或者super关键字前面可以写代码了，这是个好消息，调用构造器之前可以添加代码确保安全。

ok,正题

1.编写Java程序，打印”hello world“ 到控制台，要求保存代码和运行结果截图并上传至github

```java
package task0;

public class Test {
	void main() {
		System.out.println("hello world");
	}
}
```

图床在GitHub，加载可能会有点慢

![屏幕截图 2025-10-05 104452.png](https://github.com/neflibata-feng/img-host/blob/main/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202025-10-05%20104452.png?raw=true)

2.用IDEA创建一个Spring Boot项目，实现一个接口，通过浏览器访问`http://localhost:8080/hello`，给浏览器返回一个字符串“hello world”，要求保存代码和运行结果截图并上传至github

3.谈谈你对Java和JavaWeb的理解，它们之间有什么联系

  简单说吧，Java是一门编程语言，web编程是一个应用领域，Javaweb是使用Java进行web编程的过程；至于联系，我觉得没有什么明确的概念上的联系，完全是两个维度的概念，Java是一门全场景编程语言，所以web后端开发是他的一个应用场景这也很正常，而且，Java的异常处理使他安全、垃圾回收使他高效、JVM让他可迁移，等等优势使他非常适合web开发，所以就有了JavaWeb这个词吧。其实就我的感受而言，web不一定要跟Java高度捆绑，我觉得轻量级的web应用使用python+flask框架比Java+Springboot框架更理想，所以我更倾向于“混搭”，比如说交易或风控模块用Java+Springboot确保安全和并发性,大模型的部分用python+flask，也就是分布式开发。

