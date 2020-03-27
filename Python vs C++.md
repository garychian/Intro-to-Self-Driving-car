# Python is **dynamically typed**, C++ is **statically typed**

python
: automatically figures out variables type

C++
: need to declare the variable type before define a value. 
> Python is more for problem solving, C++ is more in base level and has fast speed. 

## Basic C++ data types
| **data type**| **declaration** | examples|
| :----        |    :----:       |   :--:  |
| integer      | int           | -20,5,700 |
| floating point   | float        | 5.109|
|double floating point|double| hold about twice decimals than floating point, but require more memory|
|character|char|a U I & @|
|boolean|bool| True or False|
|valueless|void|not for variable, used when a function don't need return anything|

## C++ functions
C++ functions consists of a **function declaration** and **function definition**.

```c++
// function declaration
returndatatype functionname(datatype variable_a, datatype variable_b, etc.);

// function definition 
returndatatype functionname(datatype variable_a, datatype variable_b, etc.){
    statement_1;
    statement_2;
    etc...
    
    return returndatatype;
}
// we don't have to put the function declaration at the top of our code to get a working solution. For doing that, we have to define our function before the main() function not after.
```
## Control statements(if, for, while, swich)
A generic **if else** statement in C++ looks like this:
```c++
if(<some criteria>){
    statement_1;
    statement_2;
    ...
}

else if(<some other criteria>){
    statement_1;
    statement_2;
    ...
}
```

### Boolean Logic
they are exactly the same.
|**operator**| **Python**|**C++**|
|:---        |   :----:   |   :----:|
|equal       |==|==|
|not equal |!=|!=|
|greater than|>|>
|less than|<|<|
|greater than or equal|>=|>=|
|less than or equal|<=|<=|
|and|and|&&|
|or|or|II |
|not|not|!|

### While
A generic while statement looks like this:
```c++
while(<some criteria>){
    statement_1;
    statement_2;
    statement_3;
    ...
}
```
### For
for loop example
```c++
// in python, the iterator was defined as: i in range(0, elapsed_time), range() generates a list of numers. 
// for C++
(int i = 0; i < elapsed_time; i++)

```
**In C++, `''` means `char`, `""` means 'string'**
