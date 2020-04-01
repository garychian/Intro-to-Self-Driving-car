# Python is **dynamically typed**, C++ is **statically typed**

python
: automatically figures out variables type

C++
: need to declare the variable type before define a value. 
> Python is more for problem solving, C++ is more in base level and has fast speed. 

## 1. Basic C++ data types
| **data type**| **declaration** | examples|
| :----        |    :----:       |   :--:  |
| integer      | int           | -20,5,700 |
| floating point   | float        | 5.109|
|double floating point|double| hold about twice decimals than floating point, but require more memory|
|character|char|a U I & @|
|boolean|bool| True or False|
|valueless|void|not for variable, used when a function don't need return anything|

## 2. C++ functions
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
## 3. Control statements
### 3.1 If/else
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

### 3.2 Boolean Logic
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

### 3.3 While
    A generic while statement looks like this:
```c++
while(<some criteria>){
    statement_1;
    statement_2;
    statement_3;
    ...
}
```
### 3.4 For
    for loop example
```c++
// in python, the iterator was defined as: i in range(0, elapsed_time), range() generates a list of numers. 
// for C++
(int i = 0; i < elapsed_time; i++)

```
**In C++, `''` means `char`, `""` means 'string'**

### 3.5 Switch (Python have no switch function)
```c++
int variable - integer;

switch(variable){
    case 1:
        code statements;
        break;
    case 2:
        code statements;
        break;
    case 3:
        code statements:
        break;
    ...

```
## 4. C++ vector
    C++ vector is like python list, we can add and remove elements from it. 
```c++
# include<vector>

int main(){
    std::vector<float> floatvectorvariable;
    return 0;
}

```
### 4.1 Initializing Vetor Values
#### 4.1.1 Declaring and Defining Simultaneously
`std::vector<int> myvector (10,6)`
#### 4.1.2 Declaring and Defining Simultaneously  with Brackets
`std::vector<float> myvector = {5.0,3.0,2.7,8.2,7.9}`
### 4.2 Vector Methods
#### 4.2.1 assign
assign helps us quickly populate a vector with fixed values.
```c++
vector<int> intvariable;
intvariable.assign(10,16);

// it going to populate the vector with 10 integers all having the value of 16
```
#### 4.2.2 push back
pushback adds an element to the end of the vector
```c++
vector<int> intvariable;
intvariable.push_back(25);
```
#### 4.2.3 size
size returns the size of the vector
`intvariable.size();`

### 4.3 Vectors and For loops
we can do things like using for loops
    - populate a vector with values
    - do math with vector
#### 4.3.1 i++ vs ++i
```c++
int i = 5;
int x = i++; // x = 5, i = 6 (called postfix)
int x = ++i; // x = 6, i = 6 (called prefiix)

//When overloading the postfix operator, C++ needs to keep track of two values. In the example, the values would be 5 and 6. For the prefix operator, C++ only needs to keep track of one value: 6. Hence, when overloading the ++ operator, it's generally more efficient to use prefix than the postfix.
```
#### 4.3.2 2D Vectors
```c++
#include <iostream>
#include <vector>

using namespace std;

int main(){
    // declare a two dimensional vector of type int
    vector <int> twovector;
    
    // setup a row
    vector<int> singlerow(3,2);
    
    // append five rows
    for (int i = 0; i < 5; i++){
        twovector.push_back(single_row);
    } 
    for (int row = 0; row < twovector.size(); row++){
        for (int col = 0; col < twovector[0].size(); col++){
            cout<<twovector[row][col]<<" ";
        }
        cout << endl;
    }
    return 0;
}

```
### 4.4 namespace
`using namespace std`
```c++
#include <iostream>
# include <vector>
# using namespace std;

int main() {
    vector<int> intvectorvariable;
    int intvariable = 5;
    cout << intvariable << endl;
    return 0;
}
```
### 4.5 Input and Output
`cout << "the result is " << endl`
`cin >> "enter a number"`

### 4.6 Reading in text files
```
1,  6,    2,   10.5
11, 15.2, 2,   21
3， 9,    1,   7.5
```
```c++
# include <iostream>
# include <fstream>
# include <string>
# include <sstream>
# include <vector>

using namespace std;

int main(){
    
    // initialize string variables for reading in text file lines
    string line;
    stringstream ss;
    
    // initializie vectors to hold the matrix
    vector<vector<float>> matrix;
    vector<float> row;
    
    // counter for characters in a text file line
    float i;
    
    // read in the file
    ifstream matrixfile("matrix.txt");
    
    // read in the matrix file line by line
    // parse the file
    
    if(matrixfile.is_open()){
        while (getline(matrixfile, line)){
            // parse the text line with a stringstream
            // clear the string stream to hold the next line
            ss.clear();
            ss.str("");
            ss.str(line);
            row.clear();
            
            // parse each line and push to the end of the row vector
            // the ss variable holds a line of text
            // ss >> i puts the next character into the i varaiable
            // the >> syntax is like cin >> some_value or cout << some_value
            // ss >> i is false when the end of the line is reached
            
            while(ss >> i){
                row.push_back(i);
                
                if (ss.peek() == ',' || ss.peek() == '')
                    ss.ignore();
                }
        }
        // push the row to the end of the matrix 
        matrix.push_back(row);
    }
    matrixfile.close();
    // print out the matrix
    for  (int row = 0; row < matrix.size(); row++){
        for(int col = 0; col < matrix[0].size();col++){
            cout << matrix[row][col] << "";
        }
        cout << endl;
    }
    else cout<< "unable to open file";
    
    return 0;
}
```
`fstream` provides functions and classes for reading in and outputting files

`sstream` provides functionality for manipulating and parsing the string


## 5. C++ Object Oriented Programming

### 5.1 Expanation of the Main.cpp
#### 5.1.1 Header

`#include <iostream>`

#### 5.1.2 Class Declaration

- The purpose of the class declaration is to give the main function access to the Gaussian class.

**we can also put class declaration into a separate .h file. Then we can just use single line of code in main.cpp** 

```c++
class Gaussian
{
    private:
        float mu, sigma2;
    public:

        // constructor functions
        Gaussian();
        Gaussian(float, float);

        // change value of average and standard deviation
        void setMu(float);
        void setSigma2(float);

        // output value of average and standard deviation
        float getMu;
        float getSigma2();

        // functions to evaluate
        float evaluate (float);
        Gaussian multply (Gaussian);
        Gaussian add(Gaussian);
};
```
##### 5.1.2.1 Private vs Public
- **private** variables are only avaible within your class code

- **public** functions and varaibles are accessible within your class and also by an object of the class

- note: there is another called **protected**, which can be accessed by any subclasses. 

- By default, C++ makes all class variables and functions private. 

- If public variables, `myguassian.mu = 25;` can change it

- If private variables, `myguassian.setmu(25)` to change the private value. 

#### 5.1.3 Main Function 
    The main function instantiates objects of the Gaussian class. So the main function uses the class whereas gaussian.cpp defined the class. 

##### 5.1.3.1 Constructor Functions
    determine how a new object will be initiated. 
```python
# This is how define in Python
def __init__(self, variable1, variable2, ... , variable10):
```

```c++
Gaussian::Gaussian(){
    mu = 0;
    sigma2 = 1;
}

Gaussian::Gaussian(float average, float sigma){
    mu = average;
    sigma2 = sigma;
}
```

##### 5.1.3.2 Class Method 
    define all of the functions that your class needs to have
```c++
void Gaussian::setMu (float average){
    mu = average;
}

void Gaussian::setSigma2 (float sigma){
    sigma2 = sigma;
}

float Gaussian::getMu(){
    return mu;
}

float Gaussian::setSigma2(){
    return sigma2;
}
```

### 5.2 Header file .h file
- Header files allowed you to put function declarations in a separate file. Ultimately, using and including header files makes it easier to re-use functions in different parts of your program. Furthermore, if the class declaration changes, you only have to change the declaration in one place.

For classes, header files serve the exact same purpose. When you use the Gaussian class in main.cpp, you can simply include the header file at the top include "gaussian.h". That gives main.cpp access to the Gaussian class.

Likewise, for gaussian.cpp, you can include the header file as well rather than writing out the entire declaration.

#### 5.2.1 Inclusion Guards
- In head files, if we use `#include"engine.h"`, it may cause main.cpp error, because some classes may declared several times in main.cpp
- As an aside, you'll notice that the header files did not use the standard namespace. It's generally recommended to avoid using namespaces in a header file. This can help avoid naming conflicts later as functions and classes are reused in different parts of a code base.

### 5.3 Implement a Class (take class Matrix as an example) 
#### 5.3.1 Class Variables
```c++
// matrix.h
class Matrix
{
    private:
        std::vector<std::vector<float>> grid;
        std::vector<float>::size_type rows;
        std::vector<float>::size_type cols;
        // The value that goes inside the brackets <> is based on whatever the original vector declaration was.
        // A size_type variable is actually an unsigned int. The size_type variable is guaranteed to be able to hold up to the maximum size of a float vector.
}
```
#### 5.3.2 Class Functions
- To write a function, we need declare those function first, these functions could be three categrries:
1. constructor functions
    constructor functions are for initializing objects
        
```c++
// declare in head file
matrix();

// define in cpp file
Classname::Classname(datatype variable1, datatype variable2){
    constructor function definition
}
```
2. set and get functions
    for accessing and assigning values to private variables

3. functions for Matrix functionality
    like: printing out the matrix, adding matrices together, multiplying matrices etc

**function declarations should go inside the class declaration**

```c++
// matrix.h
#include< vector>
#include<iostream>
#include<stdexcept>

class Matrix
{
    private:
        std::vector<std::vector<float>> grid;
        std::vector<float>::size_type rows;
        std::vector<float>::size_type cols;
        // The value that goes inside the brackets <> is based on whatever the original vector declaration was.
        // A size_type variable is actually an unsigned int. The size_type variable is guaranteed to be able to hold up to the maximum size of a float vector.

    public:

        // constructor function declarations
        // Classname(datatype variables1, datatype variable 2, ...)
        matrix();
        matrix(std::vector<std::vector<float>>);

        // set and get function declarations
        void setGrid(std::Vector<std::vector<float>>);

        std::vector<std::vector<float>> getGrid();
        std::Vector<float>::size_type getRow();
        std::vector<float>::size_type getCols();

        // matrix function declarations
        std::vector<std::vector<float>> matrix_transpose();
        std::Vector<std::vector<float>> matrix_addition(Matrix);
        void matrix_print();
};
```
```c++
// matrix.cpp
#include "matrix.h"

Matrix::Matrix(){
    std::vector <std::vector<float>> initial_grid (10, std::vector <float>(5,0,5));
    grid = initial_grid;
    rows = initial_grid.size();
    cols = initial_grid[0].size();
}

Matrix::Matrix(std::vector <std:: vector<float>> initial_grid){
    grid = initial_grid;
    rows = initial_grid.size();
    cols = initial_grid[0].size();
}

void Matrix::setGrid(std::Vector<std::vector<float>> new_grid){
    grid = new_grid;
    rows = new_grid.size();
    cols = new_grid[0].size();
}

std::vector<std::vector<float>> Matrix::getGrid(){
    return grid;
}

std::vector<float>::size_type Matrix::getRows() {
    return rows;
}

std::vector<float>::size_type Matrix::getCols() {
    return cols;
}

Matrix Matrix::matrix_transpose() {
    std::vector< std::vector<float> > new_grid;
    std::vector<float> row;

    for (int i = 0; i < cols; i++) {
        row.clear();

        for (int j = 0; j < rows; j++) {
            row.push_back(grid[j][i]); 
        }
        new_grid.push_back(row);
    }

    return Matrix(new_grid);
}

Matrix Matrix::matrix_addition(Matrix other) {

    if ((rows != other.getRows()) || (cols != other.getCols())) {
        throw std::invalid_argument( "matrices are not the same size" );
    }

    std::vector< std::vector<float> > othergrid = other.getGrid();

    std::vector< std::vector<float> > result;

    std::vector<float> new_row;

    for (int i = 0; i < rows; i++) {
        new_row.clear();
        for (int j = 0; j < cols; j++) {
            new_row.push_back(grid[i][j] + othergrid[i][j]);
        }
        result.push_back(new_row);
    }

    return Matrix(result);
}

void Matrix::matrix_print() {

    std::cout << std::endl;

    for (int i = 0; i < rows; i++)
    {
        for (int j = 0; j < cols; j++)
        {
            std::cout << grid[i][j] << " ";
        }
        std::cout << std::endl;
    }
    std::cout << std::endl;
}

```
####5.3.3 Instantiate an object
```c++
Classname objectname (inputs from initializing an object of Classname);
```
Then we can access  any public variables like
```c++
objectname.variablename
```
access public functions like
```c++
objectname.methodname(inputs)
```


# Performance Programming C++
## C++ Intro to optimization
### Intro to Computer hardware
#### Compliers and Optimization
C++ complier rewrites our code into binary instructions. The purpose pf optimizations:
    - Make the code run faster
    - Use less memory
    - Consume less electric power
#### Hardware Limitations
Some computer architectures use an approximation that directly on the CPU's arithmetic/logic unit, we may get our code to run faster.
    - CPU (Central processing unit)
        - Control Unit
            Carries out the instructions contained in our code
        - Arithmetic/ Logic Unit(ALU)
            Calcuates mathmatical and logical expressions
    - RAM 
        Store variables and instructions to support excution of program 

### Binary
|Type|bytes|Value range|
|:---|  :--:  | :---:|
|char|2 byte (8 bits))|signed (-128 to 127), unsigned(0 to 255)|
|int (16)|2 bytes(16 bits)|signed (-32768 to 32767), unsigned(0 to 65535)|
|int (32)|4 bytes(32 bits)|signed (-2147483648 to 2147483647), unsigned(0 to 4294967295)|
|float (32)|4 bytes(32 bits)|signed (-2147483648 to 2147483647), unsigned(0 to 4294967295)|
Note: If your CPU uses a 32-bit architecture, you can still create 64-bit variables in your programs as long as your compiler has this feature. But, the code will most likely run more slowly than using a 64-bit architecture with 64-bit variables. On a 32 bit system, the compiler has to create extra instructions to move and do math on 64-bit variables.

### Memory and the CPU
#### Stack
When you declare a variable in C++ --> variable will be placed on the stack --> when the function terminates --> the variable is removed from stack
Note: 
    - Stack follows FIFO rule
    - The stack is tends to be small, reason: is good for multi-threading.  
#### Heap
The heap, on the other hand, is only limited by the amount of RAM currently available. So variables that hold a lot of memory have to go on the heap.
Note: variables declare in heap should be deleted manually, otherwise it will cause crash. 
And heap is slower than stack.  

#### Dynamic Memory allocation
Dynamic memory allocation refers to when you assign variables to memory manually, these variables will go on the heap rather than the stack.
Example of dynamic memory allocation using pointers:
```c++
#include <iostream>

int main(){
    // asterisk syntax creates a pointer variable, which can hold a memory address
    int * pointervariable;

    // new is used to create a variable on the heap. This line assign an addresss to
    // pointervariable and reserves enough space told hold an ineger.
    pointervariable = new int;

    // pointer variable holds an addresss. The address allows placing a value in memory 
    // at the address.
    *pointervariable = 10;

    std::cout << "pointer value: " << *pointervariable<< "\n";
    std::cout <<"pointer address: " << pointervariable<<"\n";

    // remove pointervariable from the heap
    delete pointervariable;
    pointervariable = NULL;

    return 0;
}
```
## C++ Optimization Practice
### Software Development steps:
    - Code design
    - Implementing the design 
    - Testing for bugs and fixing the bugs
    - Optimization
### Optimization Techniques
    - Remove Dead(non-used) Code
    - Avoid Extra if statements
```c++
int x = 5;
if (x >= 5) {x = x +1;}
if (x < 5){x = x -1;}

// this is not efficient, use if and else
```
    - Avoid Nested for loops
    - Avoid Creating Extra Variables
    - Reserve Space in Memory for Vectors
    - Passing Variables by Reference
        Whenever you call a function, C++ copies any input variables into memory even if those variables are already in memory. For fundamental data types like int, char, or float, this might not be a problem.But with variables that take up a more significant amount of space, such as vectors, the extra copying can slow down your programs. 
    - Using Static
        Instead of calculating the variables over and over again, you can declare these variables as static. When the function is called the first time, C++ stores the values in memory and re-uses the values every time the function is called.

