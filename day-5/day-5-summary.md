## Strings as Array of Chars
- There's no built-in string data type in C.
- You can declare an array of characters, like this.
```c
char my_string[] = {"S","t","r","i","n","g","\0"};
//should include the null terminator

char my_string[] = "String";
// the null terminator '\0' is automatically appended

```

## Declaring Strings [Strings are char arrays]
```c
char str1[] = "string1";
char *str2 = "string2";
```
- The value of the array name `str1` is the address of the first char in the array `str1` - the starting location in the string.
- However, `str2` is a pointer to an array of chars.
- So it points to the starting address of the char array.

Look at the following code:
```c
#include <stdio.h>

int main()
{
    char str1[] = "string1";
    char *str2 = "string2";
    
    printf("%d %d %s \n",str1, &str1, str1);
    printf("%d %d %s \n",str2, &str2, str2);

    return 0;
}
```
- You'll see that `str1 = &str1 //as int` but `str2 ≠ &str2`.
- The value of `str2` is the address of the string - that is, the first char in the string.
- The address of `str2` is a different memory location altogether.
- Put simply, a pointer variable holds the address of, or points to another variable in memory.

## Strings & Functions
### Passing strings to functions
```c
void func(char anystring[]){

    }
    
    //OR
    
void func(char *anystring){

    }
```
### Returning strings from functions
To return a string from a function, set return type to `char *`.
```c

char * this_func(params){
    //statements;
    return <any_string>;
    }
```

## String vs Char - Let's understand!
```c
'a' // a single character

"a" // a string literal 
// Though "a" is a string that's one char long, 
// it points to the beginning of an array of chars in memory
```


## Declare strings on the heap
- All local variables declared inside a function are allocated memory on the stack.
- These variables are destroyed once you exit the function.
- The `malloc()` function can be used to declare memory on the heap.
- Unlike variables on the stack, the variables in heap exist even after you exit the function.

```c
s = (char *)malloc(num_chars) // as char takes up one byte, it suffices to specify num_chars only, else
s = (char *)malloc(num_elts * sizeof(<dtype>))
```

## String Functions

### Use header file `<string.h>`
To use built-in string functions, include the header file `string.h`
### Common String Functions
|Function|Syntax|Description|
|---|---|---|
|`strlen()`|`strlen(<str>)`|Returns length of `<str>`|
|`strcat()`|`strcat(<to_this>,<add_this>)`|Concatenates 2 strings|
|`strncat()`|`strcat(<to_this>,<add_this>,n)`|Concatenates `n` chars from `<add_this>` to `<to_this>`|
|`strcpy()`|`strcpy(<dest>,<src>)`|Copies `<src>` str to `<dest>` str|
|`strncpy()`|`strncpy(<dest>,<src>,n)`|Copies first `n` chars of `<src>` str to `<dest>` str|
|`strstr()`|`strstr(this,pattern)`|Returns a ptr to the starting location of `pattern` if found|

**Note**: When using string functions, ensure that the destination string has enough memory to hold the resultant.

### Use header file `<ctype.h>`
To use built-in functions on single characters, include the header file `ctype.h`
### Common Char Functions
|Function|Checks for|
|----|----|
|`isalnum()`| An alphabetic letter or a digit|
|`isalpha()`| An alphabetic letter|
|`isblank()`| A space or tab character|
|`iscntrl()` |A control character|
|`isdigit()` |A digit|
|`isgraph()`| Any printing character except a space|
|`islower()` |A lowercase letter|
|`isprint()` |Any printing character including a space|
|`ispunct()`| A printing character that is not a space or alphanumeric|
|`isspace()`| A whitespace character ( ‘ ‘, ‘\n’, ‘\t’, ‘\v’, ‘\r’, ‘\f’)|
|`isupper()`| An uppercase letter|
|`isxdigit()`| A hexadecimal digit|
