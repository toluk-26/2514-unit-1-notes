# notes
## ascii
has an offset of 48 when going to-from decimal to ascii code. 
>"0"=48

## limit precision 
```cpp
std::setw(2) << std::setfill('0')
```

## boolean input types
https://cplusplus.com/reference/cctype/
![[Pasted image 20231212164635.png]]
## float math in int
not confirmed, but using ``int value round(math*math)`` to do math with float works 
## const
makes it so that the function won't modify it `std::vector<Item> filterOutOfStockItems(const std::vector<Item>& items)`
## state machines
1. use a enum with all possible state including the finish state
	`enum states{ state1, state2, done};`
2. start state machine with first state before loop
	`states state = states::state1`
3. loop
	```cpp
	while (state != states::done){
		switch(state)
			case states::state1
				state = states::state2;
				break;
			case states::state2
				state = states::done
				break;
			case states::done
				break;
		}
	```
## reference and pointers
exer092
print or store the address of a variable `std::cout << &i;`
create a pointer var that will affect the original var `int* ptr = i`;

# syntax
## cout/cin
```cpp
    std::cout << "Enter three integers: ";
    std::cin >> i1;
```
## length/size
you can use .length() or .size() to find the length of a array/vector **counting from 1**
```cpp
std::string word = "word";
word.length(); // return 4
word[2] // return "r"
```
## math
```cpp
#include <cmath>
abs();
round();
sqrt();
log(); // its actually log natural ln. use division to be in another base
exp();
```
## int math
```cpp
x=y;
x+=y;
x-=y;
x*=y;
x/=y;
x%=y;
x++;
x--;
```
## string stream
```cpp
#include <ostream> // output only
#include <istream> // input only
#include <sstream> // output and input

std::istringstream sin;
std::ostringstream sout;

void my_code(std::istringstream& sin, std::ostringstream& sout){
	sin >> input;
	sout << output;

} // used in assignments to input like cin but not rlly
```
## vectors
1. [assign()](https://www.geeksforgeeks.org/vector-assign-in-c-stl/) – It assigns new value to the vector elements by replacing old ones
	fill the vector with 10 five times
    `v.assign(5, 10);`
    output: 10 10 10 10 10
1. [push_back()](https://www.geeksforgeeks.org/vectorpush_back-vectorpop_back-c-stl/) – It push the elements into a vector from the back
2. [pop_back()](https://www.geeksforgeeks.org/vectorpush_back-vectorpop_back-c-stl/) – It is used to pop or remove elements from a vector from the back.
3. [insert()](https://www.geeksforgeeks.org/vector-insert-function-in-c-stl/) – It inserts new elements before the element at the specified position
4. [erase()](https://www.geeksforgeeks.org/vectorclear-vectorerase-c-stl/) – It is used to remove elements from a container from the specified position or range.
5. [swap()](https://www.geeksforgeeks.org/vectorat-vectorswap-c-stl/) – It is used to swap the contents of one vector with another vector of same type. Sizes may differ.
6. [clear()](https://www.geeksforgeeks.org/vectorclear-vectorerase-c-stl/) – It is used to remove all the elements of the vector container
7. [emplace()](https://www.geeksforgeeks.org/vector-emplace-function-in-c-stl/) – It extends the container by inserting new element at position
8. [emplace_back()](https://www.geeksforgeeks.org/vectoremplace_back-c-stl/) – It is used to insert a new element into the vector container, the new element is added to the end of the vector
## arrays
```cpp
constexpr int size = 4; // need the constexpr if you use a int when u set array size
int arr[size];
delete[] arr;
```
## static cast (convert to another type)
```cpp
static_cast<new_type>(input);
(float)input; // idk if it works like this line tbh
```
# snippets

```cpp
    if (choice == 1) { 
        result = add(x, y);
    } else if (choice == 2) {
        result = subtract(x, y);
    }
```

```cpp
    // inputs and parses data
    std::string input;
    std::getline(std::cin, input);
    std::stringstream ssbreaker(input);
    ssbreaker >> name >> age >> height;
```
## header
```cpp
library.h ----------------------
#ifndef library_H
#define library_H
#include <string>
  
//declare functions
std::string addBook(std::string title, std::string author);
void displayBook(std::string info);
#endif

library.cpp----------------------
#include "library.h"
#include <iostream>

std::string addBook(std::string title, std::string author) {
    return "Title: " + title + ", Author: " + author + "\n";
}
void displayBook(std::string book) {
    std::cout << book;
}

main.cpp-------------------------
#include "library.h"
int main(){
	displayBook("dune big book");
}
```
## find min/max
```cpp
        if (min > input && input > 0) { 
            min = input;
        }
        if (max < input) {
            max = input;
        }
```
another way
```cpp
int min_value {INT_MAX};  // Start with the maximum possible integer value
int max_value {INT_MIN};  // Start with the minimum possible integer value
int min{ min_value }, max{ max_value };
if (min > value) { // find min
min = value;
}
if (max < value) { // find max
max = value;
```
## factorial and set precision
```cpp
for (i = 1; i < input; i++) {
	mathden *= i; // find the new factorial i! by multiplying i(i-1)!
	mathadd += (1/mathden); // finds new sum
}
std::cout << std::setprecision(15) << mathadd;
```

## vectors 
### declare
```cpp
std::vector<int> vector(size, input);
std::vector<std::vector<int>> vecctorr(ysize, std::vector<int>(xsize, 0));
```
### 1d
```cpp
for (i = 0; i < NUM_VALUES; i++) {
	std::cin >> input;
	values[i] = input;
}
// print
    std::cout << "[ ";
for (int i = 0; i < size; i++)
        std::cout << result[i] << " ";
    std::cout << "]" << "\n";
```
### 2d
```cpp
for (int i = 1; i < ysize; i++) { // rows
	for (int j = 1; j < xsize; j++) { // columns
		// im inside
		// i is the row
		// j is the column
		std::cin >> input;
		values[i][j] = input;

		//print
		std:cout << image[i][j] << "\t";
	}
	std::cout << "\n";
}
```
### reverse
```cpp
for (int i = (NUM_VALUES-1); i >= 0; i--) {
	std::cout << values[i] << " ";
}
```

## switch
```cpp
switch (input) {
	case 0:
		// stuff
		break;
	case 1:
		// stuff
		break;
	case 2:
		// stuff
		break;
```

## enums
```cpp
enum CoffeeType {
    americano,
    espresso,
    latte,
    cappuccino,
    mocha,
};

// convert input to enum type. an int in a list[i] unless specified
int main(){
	CoffeeType selection;
	
	if (input == "americano") {
		selection = americano;
	} else if (input == "espresso") {
		selection = espresso;
	} else if (input == "latte") {
		selection = latte;
	} else if (input == "cappuccino") {
		selection = cappuccino;
	} else if (input == "mocha") {
		selection = mocha;
	} else {
		break;
	}
}
```
## struct
can be initialized anywhere
```cpp
struct CourseSection {
    std::string courseName;
    std::string depAndNum;
    std::string semester;
    int year;
    int crn;
    std::string instructor;
};

int main(){
    struct CourseSection course1; // declare struct variable
    // assign values
    course1.courseName = "Computational Engineering";
    course1.depAndNum = "ECE 2514";
    course1.semester = "Fall";
    course1.year = 2023;
    course1.crn = 83674;
    course1.instructor = "Adams";
    
   // or -----------------------------------------------------------
   struct CourseSection CourseSections[5]; // declare struct variable
    CourseSections[0] = { "Circuits and Devices", "ECE 2024", "Fall", 2023, 83667, "Jia" };
    CourseSections[1] = { "Computational Engineering", "ECE 2514", "Fall", 2023, 83674, "Adams" };
    CourseSections[2] = { "Fundamentals Digital Systems", "ECE 2544", "Fall", 2023, 83677, "Cooper" };
    CourseSections[3] = { "Intro Diff Equations", "MATH 2214", "Fall", 2023, 87183, "Pantic" };
    CourseSections[4] = { "Foundations of Physics", "PHYS 2306", "Fall", 2023, 88960, "Nelson" };
}

CourseSections[3].year; // prints 2023

// or -----------------------------------------------------------
	std::vector<CourseSection> vourseSec;
```
## files
```cpp
#include <fstream>


    std::ifstream inf(filename); // input file
    if (!inf) { // check if file exist
        std::cerr << "File " << filename << " not found";
        return 1;
    }
    
    while (inf) {// goes through each word
        std::string word;
        inf >> word; // inputs word into string to be parsed

        for (int i = 0; i < word.length(); i++) { // goes through each letter
            letter = word[i];
        }
    }
```
## move decimal place
```cpp
int value = value / 10;
```

## Test
```cpp
#include <catch2/catch_test_macros.hpp>
#include <catch2/matchers/catch_matchers_floating_point.hpp>

TEST_CASE("test name", "[code file]"){
// you dont need sections. you can put it in thise TEST_CASE part
	SECTION("section name"){
	// call
	REQUIRE(i == 0);
	}
}
```
## array
### resize array
```cpp
// resize array ass10/code.cpp
    int new_arr = new in[newSize];
    if (newSize < oldSize)// in case the arr is getting smaller
        oldSize = newSize;
        
    for (int i = 0; i < oldSize; i++) {
        if (oldSize == 0)
            continue;
        new_arr[i] = arr[i].title; // assign elements from old array to temp array
    }

    delete[] arr; // kinda like restart
    return new_arr; // return the address for the resized playlist array
```
### delete pointer array
```cpp
void deletearr(Song*& arr) {
    delete[] arr; // deletes playlist
    arr = nullptr;
}
```
### reverse array
```cpp
void reverseArray(int* arr, int size) {
    int hold{ 0 };
    int j = size - 1;

    for (int i = 0; i < j; i++) {
        hold = arr[i]; // assign temp value
        arr[i] = arr[j]; // move mirrored value
        arr[j] = hold; // reassign temp value to end
        j--;
    }

}
```
### array sum
```cpp
int arraySum(int* arr, int size) {
    int sum{ 0 };
    for (int i = 0; i < size; i++) { //find sum
        sum += arr[i];
    }
    return sum;
}
```
## classes
```cpp
// header.h-------------------------------------
#ifndef HEADER_H
#define HEADER_H

struct struct1{
	bool var0 = true;
}

class tablet{
public:
	tablet(); // constructor
// used functions
	int function1(int& input);
	void function2(int& input);
private:
	//internal functions
	void function3(int& place);
private:
	// internal variables
	int var1 = 0; // default state
	char var2 = a;
	struct1 structvar;
}
#endif

// header.cpp-------------------------------------
#include "header.h"

int tablet::function1(int& input){
	return input;
}

void tablet::function2(int& input){
	structvar.var0 = false;
}

// psuedo function for different input args
int tablet::function1(){
	return var1;
}

void tablet::function2(){
	structvar.var0 = true;
}
// main.cpp-------------------------------------
#include "header.h"

int main(){
	tablet class1;
	class1.function1(1);
}
```
## sort selection
https://en.wikipedia.org/wiki/Selection_sort
```cpp
/* a[0] to a[aLength-1] is the array to sort */
int i,j;
int aLength; // initialise to a's length
/* advance the position through the entire array */
/*   (could do i < aLength-1 because single element is also min element) */
for (i = 0; i < aLength-1; i++)
{
    /* find the min element in the unsorted a[i .. aLength-1] */
    /* assume the min is the first element */
    int jMin = i;
    /* test against elements after i to find the smallest */
    for (j = i+1; j < aLength; j++)
    {
        /* if this element is less, then it is the new minimum */
        if (a[j] < a[jMin])
        {
            /* found new minimum; remember its index */
            jMin = j;
            continue;
        }
    }
    if (jMin != i) 
    {
        swap(a[i], a[jMin]);
    }
}
```
