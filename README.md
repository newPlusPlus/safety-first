### Modern C++
Modern C++ struggles with safety allegations and loses market share.

[![](https://newplusplus.com/wh.png)](https://www.tomshardware.com/software/security-software/white-house-urges-developers-to-avoid-c-and-c-use-memory-safe-programming-languages)

# new++
new++ is a wrapper to a safe subset of C++ that will allow only the safe syntax, objects and functions offered by modern C++ while disabling or blocking any unsafe feature of C/C++.

".npp" files are written in C/C++ with only very few minor changes.

### Restore confidence
new++ projects will enforce the memory, thread and type safety offered by modern C++ and hopefully will help to regain trust in C/C++.

new++ projects may include also C/C++ files if high performance or low level programming are needed.

### new++ basics
new++ will be based on three pillars:

1. block any unsafe feature of C/C++
2. give new meaning to existing C syntax
3. a check list of known C/C++ weaknesses that ".npp" files may not include
   
### Block any unsafe feature of C/C++
When you ask a hacker to explain about software security they will answer something like "take gets() for example".

Therefore new++ will disable (among others) unsafe functions from the C standard library, manual memory management and unions.

### New meaning to existing C syntax
Some legacy C syntax will be "reused":

| C syntax | Converted to |
| -------- | ------------ |
| char *s1 = ""; | std::string s1; |
| int arr1[8]; | std::array<int, 8>; |

### Pointers in new++
new++ distinguishes between four types of pointers:

| Syntax | Meaning | Memory allocation |
| ------ | ------- | ----------------- |
| int *ptr1; | may point only to static variables | N/A |
| local int *ptr2; | may point only to local variables | N/A |
| unique int *ptr3; | declare an "std::unique_ptr" pointer | ptr3 = new(); |
| shared int *ptr4; | declare an "std::shared_ptr" pointer | ptr4 = new(); |

Unique and shared pointers point to dynamic memory allocated with the "new" operator. The "new" operator is converted to std::make_unique() and std::make_shared() respectively.

### Modern C++ objects
Therefore new++ pointers, arrays and strings are always implemented as modern C++ objects which are known to be safe.

Check list of known C/C++ weaknesses
Over the past decade thousands of scientist and engineers took part in making C++ safe and high level. However modern C++ remains riddled with pitfalls, legacy C/C++ and wide room for human mistakes.

Therefore new++ will define the list of these pitfalls so programmers, compilers and code analyzers will know to avoid them add issue warnings or errors accordingly.

### Example 1: invalid vector iterator

[Invalidated std::vector iterators](https://stackoverflow.com/questions/35938329/c-push-back-in-stdvector-while-iterating-it).

### Example 2: confusion with std::array
In the following code new++ should issue a warning: the programmer seems to mix up rows and columns and modifies copies of rows and cells:

```C
constexpr int ROWS = 8, COLS = 3;

// unintendent result: table with 3 rows and 8 columns

std::array<std::array<int, ROWS>, COLS> myTable;

int rowN = 0;
for(auto row : myTable){

	// implicitly work on duplicates of 'myTable'
	for(auto cell: row)
		cell = rowN;

	rowN++;
}
```

### Draw a line between old and new
When you provide a new++ project, the customer knows that you drew a line between old and new and that you left the C/C++ safety issues behind you.

[![](https://newplusplus.com/rust-1.png)](https://www.techspot.com/news/101739-microsoft-seeking-software-architect-port-microsoft-365-rust.html)

Embracing good practices and good code analyzer is just not enough. What C++ developers need now is new face, new name to convince the market that modern C++ is indeed safe and efficient.

### Follow me
Please follow me on https://github.com/newPlusPlus or sign up to the [Mailing List](https://newplusplus.com/mll.html) to show interest in new++.
