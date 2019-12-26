# C# Development Notes

Here are my simplified notes for C#.

## Table of Contents

1. Introduction
2. Variables
3. sdsd
4. sdsd
5. sds

<br>

****

<br/>

## Introduction

C# is an object-oriented language built by Microsoft that allows developers to build applications that run on  **.NET Framework** .  

Uses:  

Windows apps, Web services, mobile apps, web apps, client-server apps, database apps....  

Common Language Runtime (CLR) is the foundation of the .NET Framework and it manages code at execution time, providing core services like memory management, code accuracy, etc.  

C# programs use the .NET Framework **class library** to do common tasks and provide various functionalities.  

Use **Visual Studio** IDE to create C# programs

<br/>

## Printing

#### Printing on Console

Hello World

```
static void Main(string[] args)
{
   Console.WriteLine("Hello World!");
}
```

Formatted String

```
static void Main(string[] args)
{
   int x = 10;
   double y = 20;
 
   Console.WriteLine("x = {0}; y = {1}", x, y);
}
// Output: x = 10; y = 20
```

#### Console Input

```
static void Main(string[] args)
{
   string yourName;
   Console.WriteLine("What is your name?");

   yourName = Console.ReadLine();
 
   Console.WriteLine("Hello {0}", yourName);
}
```

note that Console.ReadLine() method returns a **string** value.  

May need to convert to other value types (read below)  

#### Comments

Single-line Comment

```
 // This is a comment
```

Multi-line Comment

```
/* 
line1 
line2
line3
*/
```

 <br/>

## Variables

Need to declare: **Name** & **Data type**  

name must start with a *letter* or *underscore*  

- **int** - integer
- **float** - floating point number
- **double** - double-precision version of float
- **char** - a single character; use single quote ' '
- **bool** - True or False
- **string** - a sequence of characters; use double-quote " "



##### Implicit-declaration 

Auto-declaration by compiler  (

**var** keyword

```
var num = 15;
```

##### Constants

Cannot be changed from initial assignment

```
const double PI = 3.14; 
```

```
const double PI = 3.14;
PI = 8; //error
```

<br/> 

## Conversion of Value Type

- Convert.ToDouble
- Convert.ToBoolean
- Convert.ToInt16
- Convert.ToInt32 (default int type in C# is 32-bit)
- Convert.ToInt64

<br/>

## Arithmetic Operations

##### Pre-fix & Post-fix operations

Prefix example

```
int x = 3;
int y = ++x;
// x is 4, y is 4
```

Post-fix example

```
int x = 3;
int y = x++;
// x is 4, y is 3
```

<br/>



## Conditionals & Loops

##### If-Else Loop

```
static void Main(string[] args)
{
    int x = 33;

    if (x == 8) {
       Console.WriteLine("Value of x is 8");
    }
    else if (x == 18) {
       Console.WriteLine("Value of x is 18");
    }
    else if (x == 33) {
       Console.WriteLine("Value of x is 33");
    }
    else {
       Console.WriteLine("No match");
    }
    //Outputs "Value of x is 33"
}
```

##### Switch statement

```
int num = 3;
switch (num)
{
  case 1:
   Console.WriteLine("one");
   break;
  case 2:
   Console.WriteLine("two");
   break;
  case 3:
   Console.WriteLine("three");
   break;
  default:
   Console.WriteLine("The default case");
   break;
}
//Outputs "three"
```

Note: Must have break statements. C# compilers will not compile code without break

##### For Loop

```
for (int x = 10; x < 15; x++)
{
  Console.WriteLine("Value of x: {0}", x);
}
/*
Value of x: 10
Value of x: 11
Value of x: 12
Value of x: 13
Value of x: 14
*/
```

```
for (int x = 0; x < 10; x+=3)
{
  Console.WriteLine(x);
}

/* Outputs
0
3
6
9
*/
```

Init & increment statements may be left out.

```
int x = 10;
for ( ; x > 0; x -= 3)
{
  Console.WriteLine(x);
}
```

```
int x = 10;
for ( ; x > 0 ; )
{
  Console.WriteLine(x);
  x -= 3;
}
```

##### Do-while Loop

Guaranteed to execute at least once

```
int a = 0;
do {
  Console.WriteLine(a);
  a++;
} while(a < 5);

/* Outputs
0
1
2
3
4
*/
```

##### Break vs Continue

When the **break** statement is encountered inside a loop, the loop is immediately terminated and the program execution moves on to the next statement following the loop body. ie. it breaks out of its current loop

```
int num = 0;
while (num < 20)
{
   if (num == 5)
     break;

   Console.WriteLine(num);
   num++;
}

/* Outputs:
0
1
2
3
4
*/
```

The **continue** statement skips the current iteration of the loop and continues with the next iteration

```
for (int i = 0; i < 10; i++) {
  if (i == 5)
    continue;

  Console.WriteLine(i);
}
/* Outputs:
0
1
2
3
4
6
7
8
9
*/
```

##### ? : Operator

(Condition) ? Ans1: Ans2 <br/>

**?** checks if condition is true, if true do Ans1, if false do Ans2.

```
int age = 42;
string msg;
msg = (age >= 18) ? "Welcome" : "Sorry";
Console.WriteLine(msg);
```



<br/>



## Methods

asdasdas

