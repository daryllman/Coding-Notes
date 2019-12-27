# C# Development Notes

Here are my simplified notes for C#.

## Table of Contents

1. Introduction
2. Printing
3. Variables
4. Arithmetic Operations
5. Methods
6. ....

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



#### Implicit-declaration 

Auto-declaration by compiler 

**var** keyword

```
var num = 15;
```

#### Constants

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

#### Pre-fix & Post-fix operations

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

#### If-Else Loop

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

#### Switch statement

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

#### For Loop

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

#### Do-while Loop

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

#### Break vs Continue

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

#### ? : Operator *

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

Note: Every C# program must have at least one method - the **Main** method.  

Every method declaration includes:  

- return type

- method name

- list of parameters (if any)

```
example:

static void SayHi()
{
  Console.WriteLine("Hello");
}

static void Main(string[] args)
{
  SayHi();
}
//Outputs "Hello"
```

#### With Parameters

##### Single parameter

```
static void Func(int x)
{
  Console.WriteLine(x*2);
}
static void Main(string[] args)
{
  Func(5);
  //Outputs 10
  
  Func(12);
  //Outputs 24

  Func(42);
  //Outputs 84
}
```
##### Multiple Parameters

```
static int Sum(int x, int y)
{
   return x+y;
}

static void Main(string[] args)
{
  Console.WriteLine(Sum(8, 6));
  // Outputs 14
}
```

##### Optional Arguments

You can also specify a **default value** for optional parameters.

```
static int Pow(int x, int y=2)
{
  int result = 1;
  for (int i = 0; i < y; i++)
  {
    result *= x;
  }
 
  return result;
}
//_____________________________
static void Main(string[] args)
{
  Console.WriteLine(Pow(6));
  //Outputs 36

  Console.WriteLine(Pow(3, 4));
  //Outputs 81
}
```

##### Named Arguments

If you want to be very clear about which argument/parameter you are assigning values to, you can name the arguments in the method. So you don't have to remember the order.

```
static void Main(string[] args)
{
  int res = Area(w: 5, h: 8);
  Console.WriteLine(res);
  //Outputs 40
}
```

<br/>

#### Passing Arguments

##### Passing by Arguments

(what we usually use)

```
static void Sqr(int x)
{
  x = x * x;
}
static void Main()
{
  int a = 3;
  Sqr(a);

  Console.WriteLine(a); // Outputs 3
}
```

##### Passing by Reference

Pass by **reference** copies an argument's memory address into the formal parameter. Inside the method, the address is used to access the actual argument used in the call.     

This means that changes made to the parameter affect the argument.    

To pass the value by reference, the **ref** keyword is used in both the call and the method definition:  

```
static void Sqr(ref int x)
{
  x = x * x;
}
static void Main()
{
  int a = 3;
  Sqr(ref a);

  Console.WriteLine(a); // Outputs 9
}
```

> Note that variable that is input into method is updated as well.

##### Passing by Output

**Output** parameters are similar to reference parameters, BUT they **transfer data out** of the method rather than accept data in. They are defined using the **out** keyword.   
The variable supplied for the output parameter need not be initialized since that value will not be used.    

Output parameters are useful if you need to return multiple values from a method.

```
static void GetValues(out int x, out int y)
{
  x = 5;
  y = 42;
}
static void Main(string[] args)
{
  int a, b;
  GetValues(out a, out b);
  //Now a equals 5, b equals 42
}
```

<br/>

#### Method Overloading

When you are specifying different cases with different parameters, that will be handled differently depending on the arguments passed to the methods.

```
static void Print(int a) {
  Console.WriteLine("Value: " + a);
}
static void Print(double a) {
  Console.WriteLine("Value: " + a);
}
static void Print(string label, double a) {
  Console.WriteLine(label + a);
}
// _________________________________
static void Main(string[] args) {
  Print(11);
  Print(4.13);
  Print("Average: ", 7.57);
}
```



<br/>

## Classes & Objects

#### Title 1

```
ssdsadasd
```

<br/>



## Sample

#### Title 1

```
ssdsadasd
```

<br/>



