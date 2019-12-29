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

#### Value & Reference Types

##### Value types

Built-in data types eg int and double used to declare variables are stored in a memory location called **Stack**   

eg int x = 10    

##### Reference types

**Reference** types are used to store objects. Eg. if you instantiate an object of a class, it is stored as a reference type, and these Reference types are stored in a memory location called the **Heap**. 

ie. the memory location of objects are stored in the stack, which points to a location in the heap.      

**Stack** is used for *static memory allocation*, which includes all your value types, like x.
**Heap** is used for *dynamic memory allocation*, which includes custom objects, that might need additional memory during the runtime of your program.

#### Class

an example of a class:

```
class Person {
  int age;
  string name;
  public void SayHi() {
    Console.WriteLine("Hi");
  }
}
//______________________________

static void Main(string[] args)
{
  Person p1 = new Person();
  p1.SayHi();
}
//Outputs "Hi"
```



#### Encapsulation

Encapsulation is achieved using **access modifiers**: *public, protected, default, private*     

The access modifiers define the scope and visibility of the class members.   

| Modifier           | Containing Classes | Derived Classes | Containing Assembly | Anywhere outside containing assembly |
| ------------------ | ------------------ | --------------- | ------------------- | ------------------------------------ |
| public             | Y                  | Y               | Y                   | Y                                    |
| protected internal | Y                  | Y               | Y                   | N                                    |
| protected          | Y                  | Y               | N                   | N                                    |
| private            | Y                  | N               | N                   | N                                    |
| internal           | Y                  | N               | Y                   | N                                    |



#### Constructors

A Constructor is public, does not have a return type and is automatically called

```
class Person
{
  private int age;
  public Person()
  {
    Console.WriteLine("Hi there");
  }
}
//_____________________________

static void Main(string[] args)
{
  Person p = new Person();
}
// Outputs "Hi there"
```

```
class Person
{
  private int age;
  private string name;
  public Person(string nm)
  {
    name = nm;
  }
  public string getName()
  {
    return name;
  }
}
//____________________________

static void Main(string[] args)
 {
  Person p = new Person("David");
  Console.WriteLine(p.getName());
}
//Outputs "David"
```



#### Properties

Good practice to make properties of a member **private**    

A **property** is a member that provides a flexible mechanism to read, write, or compute the value of a private field. Properties can be used as if they are public data members, but they actually include special methods called **accessors**.    

And provide special methods called **accessors**:     

**get** accessor & **set** accessor

```
class Person
{
  private string name; //field

  public string Name //property
  {
    get { return name; }
    set { name = value; }
  }
}
```

> Note that **value** is a special keyword that represents the value that is assigned to the property using the set accessor.      
>
> By coding conventions/ norm, properties have same name as the private field but with first Capital letter.  eg 'Name' property for 'name' private field

###### Can also omit any accessor. eg below property is read-only.

```
class Person
{
  private string name;
  public string Name
  {
    get { return name; }
  }
}
```

###### Properties allow flexibility to control logic of accessing variable

```
// eg. Checking & ensuring that the value of age is greater than 0.
class Person
{
  private int age=0;
  public int Age
  {
    get { return age; }
    set {
      if (value > 0)
        age = value;
    }
  }
}
```

##### Auto-Implemented Properties

If you do not need a custom logic to access variable, use the following syntax to create a private member.

```
public string Name { get; set; }
```

You do not need to declare the private field name separately as it will be auto-created by the property automatically.     

This allows easy and short declaration of private members

```
class Person
{
  public string Name { get; set; }
}
//___________________________________

static void Main(string[] args)
{
  Person p = new Person();
  p.Name = "Bob";
  Console.WriteLine(p.Name);
}
// Outputs "Bob"
```



##### Reading/ Writing

```
class Person
{
  private string name;
  public string Name
  {
    get { return name; }
    set { name = value; }
  }
}
static void Main(string[] args)
{
  Person p = new Person();
  p.Name = "Bob";
  Console.WriteLine(p.Name);
}
```



<br/>



## Arrays

###### Creating arrays

```
int[ ] myArray;
```

```
int[ ] myArray = new int[5]; 
```

After creating array, you can assign values to individual elements in array

```
int[ ] myArray = new int[5];
myArray[0] = 23;
```

You can also create arrays with initial values set already

```
string[ ] names = new string[3] {"John", "Mary", "Jessica"};
double[ ] prices = new double[4] {3.6, 9.8, 6.4, 5.9};
```
```
// Without size declaration. 
// Will be determined by the initial array given.

string[ ] names = new string[ ] {"John", "Mary", "Jessica"};
double[ ] prices = new double[ ] {3.6, 9.8, 6.4, 5.9};
```

```
// Can omit new operator too.
string[ ] names = {"John", "Mary", "Jessica"};
double[ ] prices = {3.6, 9.8, 6.4, 5.9};
```

> note: arrays are stored in curly brackets. If you need to re-assign array, use curly brackets.

<br/>

##### Using Loops for Arrays

###### for loop

```
int[ ] a = new int[10];
for (int k = 0; k < 10; k++) {
  a[k] = k*2;
}
```

```
for (int k = 0; k < 10; k++) {
  Console.WriteLine(a[k]);
}
```

###### foreach loop

```
foreach (int k in a) {
  Console.WriteLine(k);
}
```

<br/>

##### Multidimensional Arrays

```
type[, , … ,] arrayName = new type[size1, size2, …, sizeN];
```

eg. for 3x4 integer array:

```
int[ , ] x = new int[3,4];
```

###### Initialising multidimensional arrays

```
int[ , ] someNums = { {2, 3}, {5, 6}, {4, 6} }; 
```

###### Looping multidimensional arrays

```
for (int k = 0; k < 3; k++) {
  for (int j = 0; j < 2; j++) {
    Console.Write(someNums[k, j]+" ");
  }
  Console.WriteLine();
}
```

<br/>

##### Jagged Arrays

A **jagged** array is an array whose elements are arrays. i.e. array of arrays.     

eg. single-dimensional array that has 3 elements (that are single-dimensional array of integers)

```
int[ ][ ] jaggedArr = new int[3][ ];
```
Initialising array upon declaration
```
int[ ][ ] jaggedArr = new int[ ][ ] 
{
  new int[ ] {1,8,2,7,9},
  new int[ ] {2,4,6},
  new int[ ] {33,42}
};
```

Accessing individual array elements

```
int x = jaggedArr[2][1]; //42
```

<br/>

##### Array Properties & Methods

###### Length: number of elements

###### Rank: number of dimensions of the array

```
int[ ] arr = {2, 4, 7};
Console.WriteLine(arr.Length); 
//Outputs 3

Console.WriteLine(arr.Rank); 
//Outputs 1
```

Use case in loops

```
int[ ] arr = {2, 4, 7};
for(int k=0; k<arr.Length; k++) {
  Console.WriteLine(arr[k]);
}
```

###### Max(), Min(), Sum() methods

**Max** returns the largest value.  
**Min** returns the smallest value.  
**Sum** returns the sum of all elements.

```
int[ ] arr = { 2, 4, 7, 1};
Console.WriteLine(arr.Max());
//Outputs 7

Console.WriteLine(arr.Min());
//Outputs 1

Console.WriteLine(arr.Sum());
//Outputs 14
```



<br/>



## Strings

Strings can be thought of as arrays of characters.    

**Length** returns the length of the string.    
**IndexOf(value)** returns the index of the first occurrence of the value within the string.    
**Insert(index, value)** inserts the value into the string starting from the specified index.    
**Remove(index)** removes all characters in the string after the specified index.    
**Replace(oldValue, newValue)** replaces the specified value in the string.   
**Substring(index, length)** returns a substring of the specified length, starting from the specified index. If length is not specified, the operation continues to the end of the string.  
**Contains(value)** returns true if the string contains the specified value.

```
string a = "some text";
Console.WriteLine(a.Length);
//Outputs 9

Console.WriteLine(a.IndexOf('t'));
//Outputs 5

 a = a.Insert(0, "This is ");
Console.WriteLine(a);
//Outputs "This is some text"

a = a.Replace("This is", "I am");
Console.WriteLine(a);
//Outputs "I am some text"

if(a.Contains("some"))
  Console.WriteLine("found");
//Outputs "found"

a = a.Remove(4);
Console.WriteLine(a);
//Outputs "I am"

a = a.Substring(2);
Console.WriteLine(a);
//Outputs "am"

string a = "some text";
Console.WriteLine(a[2]);
//Outputs "m"
```



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

****

###### Acknowledgements: SoloLearn, StackOverflow

