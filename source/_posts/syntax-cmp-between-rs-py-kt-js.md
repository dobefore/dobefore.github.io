---
title: syntax-cmp-between-rs-py-kt-js
readmore: true
date: 2021-10-10 19:40:22
categories: program language
tags:
---

### 声明变量/常量

| rust                 | python | js            | kt                       |
| -------------------- | ------ | ------------- | ------------------------ |
| let a:u8=3;mut;const | a=3    | var a=3;const | var a:Int=3  val a:Int=3 |

### 基本数据类型

| rust                                                         | python          | js                                                  | kt                                                           |
| ------------------------------------------------------------ | --------------- | --------------------------------------------------- | ------------------------------------------------------------ |
| number: u8~u64,f32,f64;                                      | int,float       | `var a=2.0`                                         | `Byte,Short,Int,Long,Float,Double`                           |
| str:str `let a:&str="a"`, <br>String `let a="a".to_string()`, | `a="a","""a"""` | `var a="a"`                                         | `val a="a",val=b="""b"""`                                    |
| string templs `format!("{}",a)`                              | `f'{a}'`        | `let text = `Welcome ${firstName}, ${lastName}!`; ` | `val str = "$s.length is ${s.length}"`                       |
| Char `let a='a'`                                             |                 |                                                     | val a='a'                                                    |
| array `let ar=[1,2,3]`                                       | a=[1,2,3]       | `var cars = ["Porsche", "Volvo", "BMW"];`           | //[1,2,3]     `val a = arrayOf(1, 2, 3)`     <br>  //[0,2,4]     `val b = Array(3, { i -> (i * 2) })` |

### conditional control

| rust                                                         | python                                                       | js                                                           | kt                                      |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ | --------------------------------------- |
| `if  a>0 {} else if {} else {}`                              | `if a>0: elif b>0: else:`                                    | `if (a>0){}else if (a<0) {} else {}`                         | `if (a>0){}else if (a<0) {} else {}`    |
| patern match `match x {1=>0,1|2=>0,x@1..=2=>0,_=>0} let x=2;if let 1=x{}` | 3.10 `match:case (x,y) if x==y : case 2|3: case [*l]: case {**d}: case _:` | `switch () {case 0:0;break; case 1: case 2 :0;break; default:0}` | `when (x) {1,2->0 in 1..2->0 else ->0}` |

### loop

| rust                        | python                 | js                                                           | kt                                                           |
| --------------------------- | ---------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `for i in 1..2 {};while {}` | `while 1:;for i in x:` | `a=3for (i = 0; i < 5; i++);for (x in person);for (let variable of iterable);while (i < 10);do{}while()` | `for (item in collection);while() {if (i>5) break};do {}while();` |

### enum

| rust         | python                    | js   | kt                                  |
| ------------ | ------------------------- | ---- | ----------------------------------- |
| `Enum E{Q,}` | `class E(enum.Enum):E=0 ` |      | enum class RGB { RED, GREEN, BLUE } |

### funtion

| rust                                  | python                    | js                                | kt                                                |
| ------------------------------------- | ------------------------- | --------------------------------- | ------------------------------------------------- |
| definition `fn  sum(a:u8,b:u8)->u8{}` | `def sum(a,b)->int:`      | `function sum(p1, p2) {}`         | `fun sum(a: Int, b: Int): Int {}`                 |
| varargs parameters                    | `(*tuple,**kv) (1,2,a=1)` |                                   | `(vararg v:Int) vars(1,2,3,4,5)`                  |
| lambda-like                           | `sum = lambda x,y : x+y`  |                                   | `val sumLambda: (Int, Int) -> Int = {x,y -> x+y}` |
| closure `|x| -> x+1`                  |                           | `var a=1;function A(){alert(a);}` |                                                   |

### class

| rust              | python            | js                                                           | kt                                                           |
| ----------------- | ----------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| construct         | `__init(self)__:` | `constructor(name) {this.name = name;};new Car("Ford");`     | `class Runoob  constructor(name: String) {var siteName = name init{}}; class People(val name: String){} ` |
| modifiers(可见性) |                   |                                                              | classModifier: 类属性修饰符，标示类本身特性。`abstract    // 抽象类   final       // 类不可继承，默认属性 enum        // 枚举类 open        // 类可继承，类默认是final的 annotation  // 注解类`accessModifier: 访问权限修饰符 `private    // 仅在同一个文件中可见 protected  // 同一个文件中或子类可见 public     // 所有调用的地方都可见 internal   // 同一个模块中可见` |
| Inheritence       |                   | `class Model extends Car {   constructor(brand, mod) {     super(brand);     this.model = mod;   }` | `open class Base(p: Int)           // 定义基类  class Derived(p: Int) : Base(p)` |
| interface-like    |                   |                                                              | `interface MyInterface {fun b()};class Child : MyInterface {override fun b(){} }` |

