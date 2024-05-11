# `new++` the safe side of C++

#### Modern C++
Modern C++ struggles with safety allegations and loses market share.

### new++
new++ is a wrapper to a safe sub-set of C++ that will allow only the safe structures, objects and functions offered by modern C++ while disabling or blocking any unsafe feature of C/C++.

".npp" files are written in C/C++ with only very few minor additions so new++ is not a new language but a frame for ensuring safe modern C++.

### Restore confidence
new++ projects will enforce the memory, thread and type safety offered by modern C++ and hopefully will help to regain trust in C/C++. new++ projects may comprise C/C++ files when there is need for high performance or low level programming.

### new++ basics
new++ will be based on three pillars:
- block any unsafe feature of C/C++
- give new meaning to existing C syntax
- a check list of known C/C++ weaknesses that ".npp" files may not include

#### Block any unsafe feature of C/C++
When you ask a hacker to explain about software security they will answer something like "take gets() for example".

Therefore new++ will disable (among others) unsafe functions from the C standard library, manual memory management and unions.

#### New meaning to existing C syntax
Some legacy C syntax will be "reused":

| C syntax| Converted to README |
| ------ | ------ |
| char *s1 = ""; | std::string s1; |
| int arr1[8];	| std::array<int, 8>; |

#### Pointers in new++
new++ distinguishes between four types of pointers:

| Syntax | Meaning | Memory allocation
| ------ | ------- | ----------------- |
|int *ptr1;	| may point only to static variables | N/A |
|local int *ptr2; | may point only to local variables | N/A | 
|unique int *ptr3; | declare an "std::unique_ptr" pointer | ptr3 = new(); |
|shared int *ptr4; | declare an "std::shared_ptr" pointer | ptr4 = new(); |

Unique and shared pointers point to dynamic memory allocated with the "new" operator. The "new" operator is converted to std::make_unique() and std::make_shared() respectively.

#### Check list of known C/C++ weaknesses
Over the past decade thousands of scientist and engineers took part in making C++ safe and high level. However modern C++ remains riddled with pitfalls, legacy C/C++ and wide room for human mistakes.

Therefore new++ will define the list of these pitfalls so programmers, compilers and code analyzers will know to avoid them add issue warnings or errors accordingly.

#### Example 1: invalid vector iterator
Invalidated std::vector iterators .

#### Example 2: confusion with std::array
In the following code new++ should issue a warning: the programmer seems to mix up rows and columns and modifies copies of rows and cells:

```
// a table with 3 rows and 8 columns
constexpr int ROWS = 8, COLS = 3;
std::array<std::array<int, ROWS>, COLS> myTable;

int rowN = 0;
for(auto row : myTable){

	// mofidfy implicit duplicate of 'myTable'
	for(auto cell: row)
		cell = rowN;

	rowN++;
}
```

Follow me
Please follow me on https://github.com/newPlusPlus or sign up to the Mailing List on https://newplusplus.com/ to show interest in new++.

