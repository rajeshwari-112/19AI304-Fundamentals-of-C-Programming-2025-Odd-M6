# 19AI304-Fundamentals-of-C-Programming-2025-Odd-M6
# IAPR-6- Module 6 - FoC
11. Implementation of the concept of pointer to function.
12. Implementation of programs using structure and union.
13. Implementation of programs for different storage classes.
# Ex.No:26
  Develop a C program using static storage class in function with parameter and without return to display the incremental float values as indicated in the following output.
| Input | Output                                       |
|-------|----------------------------------------------|
| 1     | 101.25&nbsp;&nbsp;201.50&nbsp;&nbsp;301.75&nbsp;&nbsp;402.00&nbsp;&nbsp;502.75 |

## Aim:
To develop a C program using the static storage class in a function with a parameter and without a return value to display the required output.
## Algorithm:
Step 1: Start<br>
Step 2: Include the standard input-output library: #include<stdio.h>.<br>
Step 3:<br>
  a. Declare an integer variable `input` to store the user’s number.  <br>
  b. Inside the function `display(int n)`, declare a static float variable `base` and initialize it to 100.25.<br>
Step 4: Read an integer from the user and store it in `input`.<br>
Step 5: Call the function `display(input)` five times.<br>
Step 6: Inside the `display` function, for each call:  <br>
  a. Calculate the sum of `base` and `n`.  <br>
  b. Display the value.  <br>
  c. Increase the value of `base` by 100.25.<br>
Step 7: Repeat Step 6 for all function calls.<br>
Step 8: Stop<br>
## Program:
```
#include <stdio.h>
void display(int n){
    static float base=100.25;
    printf("%.2f  ",base+n);
    base+=100.25;
}
int main(){
    int x; scanf("%d",&x);
    for(int i=0;i<5;i++) display(x);
    return 0;
}
```
## Output:
<img width="407" height="55" alt="image" src="https://github.com/user-attachments/assets/851ecfec-50e8-48d7-aea0-0c179eb2b268" />

## Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.


# Ex.No:27
  Implement a C program to perform arithmetic operations (addition, subtraction, multiplication, division) on two integers using function pointers. The user should input two numbers and select the desired operation from a menu.
## Aim:
  To implement a C program that uses function pointers to perform arithmetic operations (add, subtract, multiply, divide) on two integers based on user choice.
## Algorithm:
Step 1: Start<br>
Step 2: Include the standard input-output library: #include<stdio.h>.<br>
Step 3: Declare four functions to perform arithmetic operations:  <br>
  - `add(int a, int b)`  <br>
  - `subtract(int a, int b)` <br> 
  - `multiply(int a, int b)`  <br>
  - `divide(int a, int b)`<br>
Step 4: Declare a function pointer `int (*operation)(int, int)` to point to any of the arithmetic functions.<br>
Step 5: Input two integers from the user (`num1` and `num2`).<br>
Step 6: Display a menu for the user to choose an operation:  <br>
  - Add  <br>
  - Subtract <br> 
  - Multiply  <br>
  - Divide<br>
Step 7: Read the user’s choice.<br>
Step 8: Use a switch statement to assign the function pointer `operation` to the appropriate function based on the user’s choice.  <br>
  - Step 8.1: If the choice is 4 (divide), check if the second number is zero. If yes, display an error and terminate.  <br>
  - Step 8.2: If the choice is invalid, display an error and terminate.<br>
Step 9: Call the function using the function pointer and store the result in a variable `result`.<br>
Step 10: Display the result.<br>
Step 11: Stop<br>
## Program:
```
#include <stdio.h>
int add(int a,int b){return a+b;}
int sub(int a,int b){return a-b;}
int mul(int a,int b){return a*b;}
int divi(int a,int b){return a/b;}
int main(){
    int a,b,ch; scanf("%d%d",&a,&b);
    scanf("%d",&ch);
    int (*op)(int,int);
    switch(ch){
        case 1: op=add; break;
        case 2: op=sub; break;
        case 3: op=mul; break;
        case 4: if(b==0){printf("Error"); return 0;} op=divi; break;
        default: printf("Invalid"); return 0;
    }
    printf("Result=%d\n",op(a,b));
    return 0;
}
```
## Output:
<img width="117" height="114" alt="image" src="https://github.com/user-attachments/assets/3fe1b58d-eca8-43b7-bba6-ca01008eaddc" />

## Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.


# Ex.No:28
  Develop a C program to store details of n employees (employee number, name, and salary) using structures, and display the employee(s) with the highest salary. 
## Aim:
  To develop and implement a C program that uses a structure to store employee details (employee number, name, and salary) and determine the employee(s) with the highest salary.
## Algorithm:
Step 1: Start<br>
Step 2: Include the standard input-output library: #include<stdio.h>.<br>
Step 3: Define a structure `employee` with the following members:  <br>
  - `eno` (employee number)  <br>
  - `ename` (employee name)  <br>
  - `salary` (employee salary)<br>
Step 4: Declare an array of structures to store details of multiple employees.<br>
Step 5: Input the number of employees, `n`.<br>
Step 6: For each employee (`i = 0` to `n-1`), do the following:  <br>
  - Step 6.1: Input employee number.  <br>
  - Step 6.2: Input employee name (allow spaces).  <br>
  - Step 6.3: Input employee salary.  <br>
  - Step 6.4 (Optional): Print the entered details for verification.<br>
Step 7: Initialize a variable `high` with the salary of the first employee.<br>
Step 8: For each employee (`i = 1` to `n-1`), do the following:  <br>
  - Step 8.1: Compare employee salary with `high`.  <br>
  - Step 8.2: If the salary is greater than `high`, update `high` with this salary.<br>
Step 9: Print the details of employee(s) whose salary matches `high`:  <br>
  - Step 9.1: Loop through all employees.  <br>
  - Step 9.2: If employee salary equals `high`, print employee number, name, and salary.<br>
Step 10: Stop<br>
## Program:
```
#include <stdio.h>
struct emp{int eno; char name[20]; float sal;};
int main(){
    int n; scanf("%d",&n);
    struct emp e[n]; float high=0;
    for(int i=0;i<n;i++){
        scanf("%d %s %f",&e[i].eno,e[i].name,&e[i].sal);
        if(e[i].sal>high) high=e[i].sal;
    }
    printf("Highest Salary Employees:\n");
    for(int i=0;i<n;i++) if(e[i].sal==high)
        printf("%d %s %.2f\n",e[i].eno,e[i].name,e[i].sal);
    return 0;
}
```
## Output:
<img width="271" height="167" alt="image" src="https://github.com/user-attachments/assets/866c6dd7-c138-40a4-b066-f1c4c3ca5306" />

## Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.


# Ex.No:29
  Create the C program to calculate the present age of a person by passing structure as a reference.
## Aim:
  To create a C program that uses a structure to store the current date and birth date, and to calculate the person’s present age in years, months, and days by passing the structure as a reference.
## Algorithm:
Step 1: Start<br>
Step 2: Include the standard input-output library: #include<stdio.h>.<br>
Step 3: Define a structure named `date` with members to store:  <br>
  - Current date (`c_date`, `c_month`, `c_year`)  <br>
  - Birth date (`b_date`, `b_month`, `b_year`)  <br>
  - Calculated age (`cal_date`, `cal_month`, `cal_year`)<br>
Step 4: Initialize a structure variable with the current date and birth date values.<br>
Step 5: Pass the structure variable to a function `findAge()` by reference.<br>
Step 6: Inside `findAge()`:  <br>
  - a. Declare an integer array `month[]` to store the number of days in each month.  <br>
  - b. If the birth date is greater than the current date:  <br>
     - Add the number of days of the previous month to the current date.  <br>
     - Decrease the current month by 1.  <br>
  - c. If the birth month is greater than the current month:  <br>
     - Decrease the current year by 1.  <br>
     - Add 12 to the current month.  <br>
  - d. Calculate the age in days, months, and years by subtracting the corresponding birth values from the current values.<br>
Step 7: Return the structure pointer containing the calculated age.<br>
Step 8: Display the calculated age (years, months, and days) in the `main` function.<br>
Step 9: Stop<br>
## Program:
```
#include <stdio.h>
struct date{int c_d,c_m,c_y,b_d,b_m,b_y,a_d,a_m,a_y;};
void findAge(struct date *d){
    int month[]={31,28,31,30,31,30,31,31,30,31,30,31};
    if(d->b_d>d->c_d){ d->c_d+=month[d->c_m-2]; d->c_m--; }
    if(d->b_m>d->c_m){ d->c_y--; d->c_m+=12; }
    d->a_d=d->c_d-d->b_d;
    d->a_m=d->c_m-d->b_m;
    d->a_y=d->c_y-d->b_y;
}
int main(){
    struct date d;
    scanf("%d %d %d",&d.c_d,&d.c_m,&d.c_y);
    scanf("%d %d %d",&d.b_d,&d.b_m,&d.b_y);
    findAge(&d);
    printf("Age: %d Years %d Months %d Days\n",d.a_y,d.a_m,d.a_d);
    return 0;
}
```
## Output:
<img width="314" height="82" alt="image" src="https://github.com/user-attachments/assets/0fdf66d9-5c6e-4550-87d0-272f8894714a" />

## Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.


# Ex.No:30
  Build a C program to demonstrate the use of a pointer to a union. Store an integer value in a union, access it using a union pointer, and display it as both an integer and a character.
## Aim:
  To build a program in C that uses a pointer to a union to store an integer value and display it in both integer and character format.
## Algorithm:
Step 1: Start<br>
Step 2: Include the standard input-output library: #include<stdio.h>.<br>
Step 3: Define a union `abc` with the following members:  <br>
  - `int a`  <br>
  - `char b`<br>
Step 4: Declare a union variable `var` of type `abc`.<br>
Step 5: Declare a pointer `ptr` of type `union abc*`.<br>
Step 6: Assign the address of `var` to `ptr`.<br>
Step 7: Store an integer value (e.g., 90) in `var.a`.<br>
Step 8: Access and print the value of `a` using the pointer `ptr` in integer format.<br>
Step 9: Access and print the same value using the pointer `ptr` in character format.<br>
Step 10: Stop<br>
## Program:
```
#include <stdio.h>
union abc{int a; char b;};
int main(){
    union abc var,*ptr; ptr=&var;
    var.a=90;
    printf("Integer=%d\n",ptr->a);
    printf("Character=%c\n",ptr->a);
    return 0;
}
```
## Output:
<img width="126" height="54" alt="image" src="https://github.com/user-attachments/assets/0cfb69f9-5642-4d98-943d-6471343e6b0a" />

## Result: 
Thus, the program was implemented and executed successfully, and the required output was obtained.
