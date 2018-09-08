---
title: "C: Imperative Programming in Low Level"
date: 2018-08-21T16:50:59-03:00
author: "Amintas Victor"
type: "post"
---

C is a general purpose, staticly typed, imperative programming language. Also, it’s a low level language meaning it provides constructs which map efficiently to typical machine instructions. Basically it’s a more user friendly way to write low level programs. Instead of write low level code in an assembly language, you can abstract a lot and write equivalent programs in C.

<!--more-->

Because it’s so low level, many operating system kernals, and even other programming languages are implemented at least in part, using C. Also, many modern programming languages today borrow syntax and best practices from C.


# Running C Programs

We need to compile the C code down into machine code readable by the computer to run a program written in this language.

```bash
  gcc -o runnable_file file.cpp
```
Many developers choose to write C using a basic text editor, but there are also more specilized integrated development environments, some of the most popular include **Code Blocks**, **Eclipse** and **NetBeans**.

# Main and Libraries

Each program must contain a main function that will be the starting point of the execution.

```c
  int main(){
   //your code here
   return 0;
  }
```

To make use of functions from libraries, it is necessary to use ```#include``` in the program header with this syntax:

```c
  #include <libname>
```

Libraries most used:

1. ```stdio.h``` : allow input and output of values;
2. ```stdlib.h``` : Function set for numeric conversion, pseudo-random number generation, memory allocation, process control functions and others purposes;
3. ```math.h``` : Common math set.

# Printing

```c
  printf("Hello\n");
  printf("World");
  printf("!\n");
```

We can use ```\n``` to break line.

# Variables and Data Types
Names are case-sensitive and may begin with: letters or underline. After, may include letters, numbers and underline.
Convention says: *Start with a lowercase word, then additional words are capitalized. If it’s a constant, we use uppercase words separated by underline*.

```c
  char testGrade = 'A';    // single 8-bit character.
  char name[] = "Mike";    // array of characters (string)

  // you can make them unsigned by adding "unsigned" prefix
  short age0 = 10;         // atleast 16-bits signed integer
  int age1 = 20;           // atleast 16-bits signed integer (not smaller than short)
  long age2 = 30;          // atleast 32-bits signed integer
  long long age3 = 40;     // atleast 64-bits signed integer

  float gpa0 = 2.5;       // single percision floating point
  double gpa1 = 3.5;       // double-precision floating point
  long double gpa2 = 3.5;  // extended-precision floating point

  int isTall;             // 0 if false, non-zero if true
  isTall = 1;

  const is IS_TALLER = 1; // we can use constants with the prefix "const"


  // you can format the output that way
  testGrade = 'F';
  printf("%s, your grade is %c \n", name, testGrade);
  /*
  %c	character
  %d	integer number (base 10)
  %e	exponential floating-point number
  %f	floating-point number
  %i	integer (base 10)
  %o	octal number (base 8)
  %s	a string of characters
  %u	unsigned decimal (integer) number
  %x	number in hexadecimal (base 16)
  %%	print a percent sign
  \%	print a percent sign
  */
```
# Casting and Converting

We perform casting and conversions using the following syntax:

```c
  printf("%d \n", (int)3.14);  // 3
  printf("%f \n", (double)3 / 2); // 1.0
```

# Pointers

We can manipulate the pointers using the following syntax:

```c
  int num = 10;
  printf("%p \n", &num); // num’s value (10)

  int *pNum = &num; // storing pointer
  printf("%p \n", pNum); // num’s value (10)
  printf("%d \n", *pNum); // num’s endress
```

# Numbers

We can manipulate the numbers using the following syntax:

```c
  printf("%d \n", 2 * 3);       // Basic Arithmetic: +, -, /, %, *
  printf("%d \n", 10 % 3);      
  printf("%d \n", (1 + 2) * 3);   // order of operations
  printf("%f \n", 10 / 3.0);    // int's and doubles


  int num = 10;
  num += 100;                   // +=, -=, /=, *=
  printf("%d \n",num);

  num++;                       // ++, --
  printf("%d \n", num);

  printf("%f \n", pow(2, 3));  //power
  printf("%f \n", sqrt(144));  // square root
  printf("%f \n", round(2.7)); // round number
```

# User Input

We can get and manipulate the user input using the following syntax:

```c
  // getting a array of char (String)
  char name[10];
  printf("Enter your name: ");
  fgets(name, 10, stdin);
  printf("Hello %s! \n", name);

  // getting a integer
  int age;
  printf("Enter your age: ");
  scanf("%d", &age);
  printf("You are %d \n", age);

  // getting a single char
  char grade;
  printf("Enter your grade: ");
  scanf("%c", &grade);
  printf("You got an %c on the test \n", grade);

  // getting a double
  double gpa;
  printf("Enter your gpa: ");
  scanf("%lf", &gpa);
  printf("Your gpa is %f \n", gpa);
```

# Arrays and Matrices

We can instantiate and manipulate arrays and matrices using the following syntax:

```c
  int luckyNumbers[6];                          // we can define the array’s size previously
  int luckyNumbers[] = {4, 8, 15, 16, 23, 42};  // we can define the array’s size dynamically
  //        indexes:    0  1  2   3   4   5
  luckyNumbers[0] = 90;
  printf("%d \n", luckyNumbers[0]);             // we can set the elements of an array
  printf("%d \n", luckyNumbers[1]);

  int  numberGrid[2][3];                        // we can define a matrices similarly
  int numberGrid[2][3] = { {1, 2, 3}, {4, 5, 6} };
  numberGrid[0][1] = 99;

  printf("%d \n", numberGrid[0][0]);
  printf("%d \n", numberGrid[0][1]);
```

# Functions

We use functions in this way:

```c
  int addNumbers(int num1, int num2);   // we need to declare functions before the main

  int main(){
       int sum = addNumbers(4, 60);
       printf("%d \n", sum);

       return 0;
  }

  int addNumbers(int num1, int num2){  // after main, we can implement declared functions
       return num1 + num2;
  }
```

# Conditionals

```c
  int isStudent = 0;
  int isSmart = 0;

  // if statement
  if(isStudent != 0 && isSmart != 0){
       printf("You are a student\n");
  } else if(isStudent != 0 && isSmart == 0){
       printf("You are not a smart student\n");
  } else {
       printf("You are not a student and not smart\n");
  }

  // we can do comparisons: >, <, >=, <=, !=, ==
  if(1 > 3){
       printf("number omparison was true\n");
  }
  if('a' > 'b'){
       printf("character comparison was true\n");
  }


  char myGrade = 'A';

  // switch statement
  switch(myGrade){
       case 'A':
            printf("You Pass\n");
            break;
       case 'F':
            printf("You fail\n");
            break;
       default:
            printf("Invalid grade\n");
  }
```

# Loops

We can iterate in this way:

```c
  // while loop
  int index = 1;
  while(index <= 5){
       printf("%d \n", index);
       index++;
  }

  // do-while loop
  index = 1;
  do{
       printf("%d \n", index);
       index++;
  }while(index <= 5);

  // for loop
  for(int i = 0; i < 5; i++){
       printf("%d \n", i);
  }
```

# Structs

Structs are like objects in the oo paradigm. We can use it in this way:

```c
  // defining struct
  struct Book{
       char title[100];
       char author[100];
  }

  // instantiating and manipulating struct
  int main(){

        struct Book book1;
        book1.numPages = 600;
        strcpy( book1.title, "Harry Potter" );
        strcpy( book1.author, "JK Rowling");

        printf("%s \n", book1.title);

        return 0;
  }
```

# Writing and Reading To External Files

We can manipulate external files in this way:

```c
  char line[255];

  // if the file does not exists, a new file will be created
  FILE * filePointer = fopen("PATH/file.txt", "w"); // creating/writing/overwriting a file
  FILE * filePointer = fopen("PATH/file.txt", "a"); // appending content into a file

  // we can write, overwrite or append content with this command
  fprint(fpointer, "content");

  // we can read a line of a file, one line per call
  fgets(line, 255, fpointer);

  // after use a file, we need to close the pointer
  fclose(fpointer);
```
