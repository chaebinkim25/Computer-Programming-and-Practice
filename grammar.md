# 함수선언 (매개변수리스트가 있을 때)

매개변수는 함수가 호출될 때마다 메모리 공간을 새로 할당받고 함수 실행을 종료할 때 삭제됩니다. 
매개변수의 초기값은 호출할 때 정한 값입니다. 
함수 선언은 함수의 이름, 반환타입, 매개변수의 타입을 정합니다.  
함수 선언시 매개변수의 이름은 적지 않고 타입만 적어도 됩니다. 
매개변수가 없는 함수를 선언할 때는 괄호 안에 void만 적습니다. 

`타입` `이름` `(` `매개변수리스트` `)` `;` 형태로 함수선언을 합니다.

`매개변수리스트`는 `매개변수선언` 또는 `매개변수리스트` `,` `매개변수선언` 입니다. 

`매개변수선언`은 `타입` `이름` 또는 `타입` 입니다. 

#### 코드 예시:
```c
int f(int, int); /* 반환 타입이 int고, 이름이 f고, 매개변수 두개의 타입이 모두 int인 함수의 선언 */
int g(int a, int b); /* 이름이 g고, 함수 종류는 f와 동일한 함수의 선언 */
int h(void); /* 반환 타입이 int고, 이름이 h고, 매개변수가 없는 함수의 선언 */
int x(); /* 반환 타입이 int고, 이름이 x고, 매개변수에 대해서는 정하지 않은 함수의 선언 */
```

#### 관련 C89 표준
3.5.4.3 Function declarators (including prototypes)
> Semantics
> 
> A parameter type list specifies the types of, and may declare identifiers for, the parameters of the function.
> ... The special case of void as the only item in the list specifies that the function has no parameters.

3.5 DECLARATIONS
> Constraints
>
> All declarations in the same scope that refer to the same object or function shall specify compatible types.

3.5.4.3 Function declarators (including prototypes)
> Semantics
>
> For two function types to be compatible, both shall specify compatible retury types.
> Moreover, the paremeter type lists, ... , shall agree in the number of parameters ... ;
> corresponding parameters shall have compatible types. ...

1.6 DEFINITION OF TERMS
> Parameter --- an object declared as part of a function declaration or definition
> that acquires a value on entry to the function, or ...

# 함수선언 (매개변수가 없을 때)

함수 선언은 함수 정의, 전역변수 선언과 더불어 전처리 후의 C 프로그램을 구성합니다. 
함수 선언은 이름이 특정 반환타입의 함수를 가리킨다고 정합니다. 

`타입` `이름` `(` `)` `;` 형태로 씁니다.

#### 코드 예시:
```c
/* 반환 타입이 void고, 이름이 x인 함수의 선언 */
void x();
```

#### 관련 C89 표준
3.5.4.3 Function declarators (including prototypes)
> Semantics
>
> If, in the declaration "T D1", D1 has the form
>
> D( ... )
>
> ... then the type specified for ident is " ... function returning T."

# 함수호출식 (매개변수가 없는 함수)

함수를 실행하는 것을 함수를 호출한다고 합니다. 
함수를 호출하는 것은 값을 쓰거나 더하기를 하는 것처럼 결과로 값을 얻습니다. 
실행 결과를 얻는 것을 식이라고 하고, 식은 문장의 일부로 쓰입니다. 

`식` `(` `)` 형태로 씁니다. 

`(` 왼쪽의 `식`은 함수를 가리켜야 합니다. 

#### 코드 예시:
```c
int main() {
   return main(); /* 자신을 무한히 호출해서 에러가 발생합니다 */
}
```

#### 관련 C89 표준
3.3.2.2 Function calls
> Semantics
>
> ... expression followed by parentheses () ... is a function call.
> 
> ... expression denotes the called function. ...
>
> ... Recursive function calls shall be permitted, both directly and indirectly through any chain of other functions.

# 여러 소스파일

프로그램의 코드가 여러 소스파일에 나눠져 있을 수 있습니다. 
기계어로 번역되어있는 파일에 있는 함수를 쓸 수도 있습니다. 
다른 파일에 있는 함수를 쓸 때도 함수 선언을 하고 쓰면 됩니다.

#### 코드 예시:
```c
/* main.c */

int value(int); /* 반환타입이 int고, 매개변수타입도 int인 함수 value를 선언 */

int main() {
   return value(5);
}
```

```c
/* value.c */

int value(int); /* value 함수 선언 */

/* value 함수 정의 */
int value(int x) {
   return x;
}
```

#### 관련 C 표준
2.1.1.1 Program structure
> A C program need not all be translated at the same time.
> The text of the program is kept in units called source files in this Standard.
> A source file ... is called a translation unit.
> ... The seperate translation units of a program communicate by (for example) calls to functions
> whose identifiers have external linkage,
> by manipulation of objects whose identifiers have external linkage,
> and by manipulation of data files.
> Translation units may be separately translated and then later linked to produce an executable program.

# 전역변수선언
변수는 값을 저장할 수 있는 메모리 공간입니다. 
전역변수는 소스 파일에 있는 모든 코드에서 쓸 수 있습니다. 
같은 전역변수를 여러번 선언할 경우 한번만 메모리 공간을 할당받습니다.
전역변수 선언에서 초기화를 하면 처음 메모리 공간을 할당받을 때 초기값을 저장합니다.
한 전역변수에 대해서 초기화는 한번만 할 수 있습니다. 
전역변수의 초기값으로는 상수만 쓸 수 있습니다. 

초기값이 없는 변수선언은 `타입` `이름` `;` 형태로 합니다.

초기값이 없는 변수선언은 `타입` `이름` `=` `식` `;` 형태로 합니다. 

#### 코드 예시:
```c
int x = 1; /* 초기값이 1인 int 타입의 전역변수 x를 선언하고, 메모리 공간을 할당받음 */
int x; /* int 타입의 전역변수 x를 선언. 메모리 공간은 앞에서 할당받았으므로 할당받지 않음 */

int get_x() {
   return x; /* 함수 정의의 문장리스트에서 x의 값에 접근 가능 */
}
```

# 관련 C89 표준
3.7 EXTERNAL DEFINITIONS
>
>Semantics
>
>... An external definition is an external declaration that is also a definition of a function or an object
>If an identifier declared with external linkage is used in an expressioin (...),
>somewhere in the entire program there shall exactly one external definition for the identifier.

3.7.2 External object definitions
>
>Semantics
>
>If the declaration of an identifier has file scope and an initializer,
>the declaration is an external definition for the identifier.
>
>A declaration of an identifier for an object that has file scope without an initializer, ..., constitutes a tentative definition.
>If a translation unit contains one or more tentative definitions for an identifier,
>and the translation unit contains no external definition for that identifier,
>then the behavior is exactly as if the translation unit contains a file scope declaration of that identifier,
>with an initializer equal to 0. ...

# 함수정의 (매개변수리스트가 있을 때)

함수 정의는 함수의 이름, 반환타입, 매개변수의 타입과 이름, 실행할 문장리스트를 정합니다.  
함수 실행하는 동안 매개변수에 저장된 값을 읽거나 새로운 값을 매개변수에 저장할 수 있습니다. 
매개변수는 함수를 호출할 때마다 메모리를 새로 할당받고, 호출시 전달된 값으로 초기값이 저장됩니다.
매개변수가 없는 함수를 정의할 때는 괄호 안에 void만 적거나, 괄호 안을 비워놓습니다. 

`타입` `이름` `(` `매개변수리스트` `)` `{` `문장리스트` `}` 형태로 함수정의를 합니다.

`매개변수리스트`는 `매개변수선언` 또는 `매개변수리스트` `,` `매개변수선언` 입니다. 

`매개변수선언`은 `타입` `이름` 입니다. 

#### 코드 예시:
```c
int f(int a, int b) { return a; } /* 첫번째 매개변수를 반환하는 함수 */
int g(int a, int b) { return b; } /* 두번째 매개변수를 반환하는 함수 */
int h(void) { return 1; } /* 1을 반환하는 함수 */
```

### 관련 C 표준
3.7.1 Function definitions
> Constraints
>
> If the declarator includes a parameter type list,
> the declaration of each parameter shall include an identifier
> (except for the specifal case of a parameter list consisting of a single parameter of type void,
> in which there shall not be an identifier).
>
> Semantics
>
> ... parameter type list ... specifies the types of all the parameters;
> ... also servers as a function prototype for later calls to the same function in the same translation unit.
> ...
> 
> On entry to the function the value of each argument expression shall be converted to the
> type of its corresponding parameter, as if by assignment to the parameter. ...

# <stdio.h> 라이브러리의 printf 함수
<stdio.h> 헤더 파일에는 입력과 출력에 관련된 함수들의 선언이 있습니다. 
printf함수는 콘솔창에 문자열을 표시할 수 있고, 표시할 문자열 안에 값들을 넣을 수 있습니다. 
printf함수의 반환값은 출력한 문자의 개수이며, 에러가 발생했을 때는 음수가 반환됩니다.
printf함수는 가변 개수 매개변수라는 문법으로 선언 및 정의되어 있어서 매개변수의 개수는 한개 이상이면 모두 가능합니다.

printf 함수를 호출할 때 첫번째 매개변수에는 문자열을 씁니다. 

문자열은 `"` `문자들` `"` 형태로 씁니다. 

#### 예제 코드:
```c
int main() {
   return printf("C"); /* 화면에 C가 출력된 후 출력된 글자 개수가 반환됩니다. */
}
```

#### 관련 C89 표준
4.9.6.3 The printf function
> Description
>
> The printf function is equivalent to fprintf with the argument stdout interposed before the arguments to printf.
>
> Returns
> The printf function returns the number of characters transmitted, or a negative value if an output error occurred.

4.9.6.1 The fprintf function
> Description
>
> The fprintf function writes output to the stream pointed to by stream,
> under control of the string pointed to by format that specifies how subsequent arguments are converted
> for output. ...
>
> Returns
> The fprintf function returns the number of characters transmitted, or a negative value if an output error occrured.

4.9.1 Introduction
> stdout ... point to the ... standard ... output streams.

# 문자 값
문자 값은 문자에 해당하는 정수를 나타냅니다.   

`'` `문자` `'` 형태로 씁니다. `문자`는 작은 따옴표 `'`, 역슬래시 `\`, 엔터를 제외하고 쓸 수 있고, 특수문자 문법을 쓸 수도 있습니다. 

각 문자에 해당하는 정수는 컴파일러에서 정합니다. 

문자가 여러개 있을 경우, 한국어 사용 등의 경우에 해당하는 정수도 컴파일러에서 정합니다.  

#### 코드 예시:
```c
int c = 'a'; /* 'a'는 문자 a에 해당하는 정수 값을 의미합니다 */
```

#### 관련 C89 표준
[3.1.3.4 Character constants](https://port70.net/~nsz/c/c89/c89-draft.html#3.1.3.4)
> **Description**
>
> An integer character constant is a sequence of one or more multibyte characters enclosed in single-quotes, as in 'x' or 'ab'.
> ... With a few exceptions detailed later, the elementes of the sequence are any members of the source character set;
> they are mapped in an implementation-defined manner to members of the execution character set.
>
> **Semantics**
>
> An integer character constant has type int.
> The value of an integer character constant containing a single character that maps into a member of the basic execution character set
> is the numerical value of the representation of the mapped character interpreted as an integer.
> The value of an integer character constant containing more than one character, or containing a character or escape sequence
> not represented in the basic execution character set, is implementation-defined. ...

[2.2.1 Character sets](https://port70.net/~nsz/c/c89/c89-draft.html#2.2.1)
> Two sets of characters and their associated collating sequences shall be defined:
> the set in which source files are written, and the set interpreted in the execution environment.
> The value of the members of the execution character set are implementation-defined; ...
>
> In a character constant or string literal, members of the execution character set shall be represented by corresponding members of
> the source character set or by escape sequences consisting of the backslash \ followed by one or more characters.
> A byte with all bits set to 0, called the null character, shall exist in the basic execution character set; ...
>
> Both the basic source and basic execution character sets shall have at least the following members:
> the 26 upper-case letters of the English alphabet
>
> A B C D E F G H I J K L M
>
> N O P Q R S T U V W X Y Z
>
> the 26 lower-case letters of the English alphabet
>
> a b c d e f g h i j k l m
>
> n o p q r s t u v w x y z
>
> the 10 decimal digits
>
> 0 1 2 3 4 5 6 7 8 9
>
> the following 29 graphic characters
>
> ~ " # % & ' ( ) * + , - . / :
> ; < = > ? [ \ ] ^ _ { | } ~
>
> the space character, and control characters representing horizontal tab, vertical tab, and form feed.
>
> ... In source files, there shall be some way of indicating the end of each line of text;
> ... In execution character set, there shall be control characters representing alert, backspace, carriage return, and new line.
> If any other characters are encountered in a source file (except in a preprocessing token ... ), the behavior is undefined.

[3.1.2.5 Types](https://port70.net/~nsz/c/c89/c89-draft.html#3.1.2.5)
> ... If a member of the required source character set enumerated in 2.2.1 is ... guranteed to be positive.
> ... values are treated as ... integers.

# 정수 값
10진수, 16진수, 8진수로 정수값을 표현할 수 있습니다.   

10진수는 `1-9숫자` `0-9숫자` 형태로 씁니다. `0-9`숫자는 없어도 되고 여러개 있어도 됩니다. 

16진수는 `0x` `0-f숫자` 형태로 씁니다. `0-f`숫자는 1개 이상 있어야 합니다. 대문자로 써도 됩니다. 

8진수는 `0` `0-7` 형태로 씁니다. `0-7`숫자는 없어도 되고 여러개 있어도 됩니다. 


#### 코드 예시:
```c
int x() {
   return 0x01; /* 1을 반환합니다. */
}
```

#### 관련 C89 표준
[3.1.3.2 Integer constants](https://port70.net/~nsz/c/c89/c89-draft.html#3.1.3.2)
> **Description**
>
> An integer constant begins with a digit, but has no period or exponent part.
> It may have a prefix that specifies its base and a suffix that specifies its type.
>
> A decimal constant begins with a nonzero digits and consists of a sequence of decimal digits.
> An octal constant consists of the prefix 0 optionally followed by a sequence of the digits 0 through 7 only.
> A hexadecimal constant consists of the prefix 0x or 0X followed by a sequence of the decimal digits
> and the letters a (or A) through f (or F) with values 1o through 15 respectively.
>
> **Semantics**
>
> The value of a decimal constant is computed base 10; that of an octal constant, base 8;
> that of a hexadecimal constant, base 16. The lexically first digit is the most significant.
>
> The type of an integer constant is the first of the corresponding list in which its value can be represented.
> Unsuffixed decimal: int, long int, unsigned long int;
> unsuffixed octal or hexadecimal: int, unsigned int, long int, unsigned long int;
> suffixed by the letter u or U: unsigned int, unsigned long int;
> suffixed by the letter l or L: long int, unsigned long int;
> suffixed by both the letters u or U and l or L: unsigned long int.

# 특수 문자
문자 값에 들어갈 문자로 특수문자를 쓸 수 있습니다.   

특수문자에는 `\'` `\"` `\?'` `\\` `\n` `\t` 등이 있습니다.

`\'`는 작은 따옴표를, `\"`는 큰 따옴표를, `/?`는 물음표를, `\\`는 역슬래시를, `\n`은 줄바꿈을, `\t`는 탭을 의미합니다. 

#### 코드 예시:
```c
int c = '\''; /* '\''는 문자 '에 해당하는 정수 값을 의미합니다 */
```

#### 관련 C89 표준
[3.1.3.4 Character constants](https://port70.net/~nsz/c/c89/c89-draft.html#3.1.3.4)
> **Description**
>
> The double-quote and question-mark ? are representable either by themselves or
> by the escape sequences \" and "? respectively, but the single-quote ' and the backslahs \ shall be represented,
> respectively, by the escape sequences \' and \\.
>
> The octal digits that folow the backslashs in an octal escape sequence ...
>
> The hexadecimal digits that follow the backslash and the letter x in a hexadecimal escape sequence ...
>
> ... if any other escape sequence is encountered, the behavior is undefined.
>
> **Examples**
>
> The construction '\0' is commonly used to represent the null character.

[2.2.2 Character display semantics](https://port70.net/~nsz/c/c89/c89-draft.html#2.2.2)
> Alphabetic escape sequences representing nongraphic characters in the execution character set are intended to produce actions on display devices as
> ... ( "new line" ) Moves the active position to the initial position of the current line.

# 지역변수선언
지역변수는 함수 안에서 쓴다고 선언된 변수입니다. 
지역변수를 선언하는 문법과 전역변수를 선언하는 문법은 똑같습니다.

초기값이 없는 변수선언은 `타입` `이름` `;` 형태로 합니다.

초기값이 없는 변수선언은 `타입` `이름` `=` `식` `;` 형태로 합니다. 

#### 코드 예시:
```c
void f() {
   int x = 1; /* f 함수를 실행할 때마다 새로 할당되고 없어지는 변수 x */
}

void g() {
   int x = 2; /* g 함수를 실행할 때마다 새로 할당되고 없어지는 변수 x */
}
```

# 관련 C89 표준
3.1.2.1 Scopes of identifiers
>
> An identifier is visible (i.e., can be used) only within a region of program text called its scope.
> There are ... kinds of scopes: ... , file, block, and function prototype.
> (A function prototype is a declaration of a function that declares the types of its parameters).
>
> ... identifier has scope determined by the placement of its declaration ...
> If the declarator ... that declares the identifier appears outside of any block or list of parameters,
> the identifier has file scope, which terminates at the end of the translation unit.
> If the declarator ... that declares the identifier appears inside a block or
> within the list of parameter declarations in a function definition,
> the identifier has block scope, which terminates at the } that closes the associated block.
> If the declarator ... that declares the identifier appears within the list of parameter declarations
> in a function prototype (not part of a function definition), the identifier has function prototype scope,
> which terminates at the end of the function declarator.
> If an outer declaration of a lexically identical identifier exists in the same name space,
> it is hidden until the current scope terminates, after which it again becomes visible.

3.1.2.2 Linkage of identifiers
>
> An identifier declared in different scopes or in the same scope more than once can be made to refer
> to the same object or function by a process called linkage. There are three kinds of linkage:
> external, internal, and none.
>
> In the set of translation units and libraries that constitutes an entire program,
> each instance of a particular identifier with external linkage denotes the same object or function.
> Within one translation unit, each instance of an identifier with internal linkage denotes the
> same obejct or function.
> Identifiers with no linkage denote unique entities.
>
> The following identifiers have no linkage: ... an identifier declared to be a function parameter;
> an identifier declared to be an object inside a block witout the storage-class specifier extern.

3.1.2.4 Storage durations of objects
>
> an object has a storage duration that determines its lifetime.
> There are two storage durations: static and automatic.
> An object declared with no linkage and without the storage-class specifier static has
> automatic storage duration. Storage is guaranteed to be reserved for a new instance of such an object
> on each normal entry into the block in which it is declared ...
> If an initialization is specified for the value stored in the object, it is performed on each normal entry
> ... Storage for the object is no longer guaranteed to be reserved when execution of the block ends in
> any way. (Entering an enclosed block suspends but does not end execution of the enclosing block.
> Calling a function that returns suspends but does not end execution of the block containing the call.)
> The value of a pointer that referred to an object with automatic storage duration that is no longer
>guranteed to be reserved is indeterminate. 

1.6 DEFINITIONS OF TERMS
> Object ---  region of data storage in the execution environment, the contents of which can represent
> values. Except for bit-fields, objects are compsoed of contiguous sequences of one or more bytes,
> the number, order, and encoding of which are either explicitly specified or implementation-defined.

# 주소 연산식
주소 연산은 변수나 함수의 주소를 계산합니다.

`&` `식` 형식으로 씁니다. 

`식`은 변수나 함수를 가리켜야 합니다. 

주소 연산 결과의 타입을 포인터라고 합니다. 

#### 코드 예시:
```c
int i = 0; /* int 타입의 전역변수 i, 초기값은 0 */
int *pi = &i; /* int 포인터 타입의 전역변수 pi, 초기값은 i의 주소 */
```

#### 관련 C89 표준
[3.3.3.2 Address and indirection operators](https://port70.net/~nsz/c/c89/c89-draft.html#3.3.3.2)
> **Constraints**
> 
> The operand of the unary & operator shall be either a function designator or an lvalue that designates an object ...
>
> **Semantics**
>
> The result of the unary & (address-of) operator is a pointer to the object or function designated by
> its operand. If the operand has type " type ", the result has type "pointer to type ".

[3.2.2.1 Lvalues and function designators](https://port70.net/~nsz/c/c89/c89-draft.html#3.2.2.1)
> An lavalue is an expression (with an object type ...) that designates an object. ...
> Except when it is the operand of ... the unary & operator, ... an lavalue ... is converted to the
> value stored in the designated object (and is no longer an lvalue).

# 문자 타입
문자 타입은 소스 파일의 문자들을 저장할 수 있는 크기인 1바이트를 가지며, 이진수로 표현됩니다.  

문자 타입은 정수 타입의 일종입니다. 

#### 코드 예시:
```c
char c = 'a'; /* 변수 c는 1 바이트의 메모리 공간을 할당받습니다 */
```

#### 관련 C89 표준
[3.1.2.5 Types](https://port70.net/~nsz/c/c89/c89-draft.html#3.1.2.5)
> The meaning of a value stored in an object or returned by a function is determined by the type of the expression used to access it.
> (An identifier declared to be an object is the simplest such expression; the type is specified in the declaration of the identifier.)
> Type are partitioned into object types (types that describe objects), function types (types that describe functions), and incomplete types
> (types that describe objects but lack information needed to determine their sizes).
>
> An object declared type char is large enough to store any member of the basic execution character set.
> If a member of the required source character set enumerated in 2.2.1 is stored in a char object, its value is guranteed to be positive. ...
>
> The type char, ... are collectively called integral types. The representations of integral types shall define values by use of
> a pure binary numeration system. ...

[3.3.3.4 The sizeof operator](https://port70.net/~nsz/c/c89/c89-draft.html#3.3.3.4)
> ... the size (in bytes) of
>
> ... type char ... is 1. ...

[1.6 DEFINITIONS OF TERMS](https://port70.net/~nsz/c/c89/c89-draft.html#1.6)
> \* Byte --- the unit of data storage in the execution environment large enough
> to hold any member of the basic character set of the execution environment.
> It shall be possible to express the address of each individual byte of an object uniquely.
> A byte is composed of a contiguous sequence of bits,
> the number of which is implementation-defined.
> The least significant bit is called the low-order bit,
> the most significant bit is called the high-order bit.

[2.2.4.2 Numerical limits](https://port70.net/~nsz/c/c89/c89-draft.html#2.2.4.2)
> ... Their implementation-defined values shall be equal or greater in magnitude (absolute value) to those shown, with the same sign.
> \* maximum number of bits for smallest object that is not a bit-field (byte) CHAR_BIT 8

# 배열 타입
배열 타입은 같은 타입 여러개를 메모리에 차례로 늘어놓은 것을 뜻합니다.

`타입` `이름` `[` `식` `]` `;` 형태로 배열을 선언할 수 있습니다.

여기서 식은 상수로 계산되어야 합니다.

#### 코드 예시:
```c
char ca[10]; /* char 타입 10개를 늘어놓은 배열 ca를 전역변수로 선언합니다. */
```

#### 관련 C89 표준
[3.1.2.5 Types](https://port70.net/~nsz/c/c89/c89-draft.html#3.1.2.5)
> An array type describes a contiguously allocated set of objects with a particular member object type, called the element type.
> Array types are characterized by their element type and by the number of members of the array.
> An array type is said to be derived from its element type, and if its element tye is T,
> the array type is sometimes called "array of T".
> The construction of an array type from an element type is called "array type derivation".
>
> An array type of unknown size is an incomplete type. It is completed, for an identifier of that type,
> by specifying the size in a later declaration (with internal or external linkage).
>
> Array, function, and pointer types are collectively called derived declarator types.
> A declarator type derivation from a type T is the construction of a derived declarator type from T by the application
> of an array, a function, or a pointer type derivation to T.

[3.5.4.2 Array declarators](https://port70.net/~nsz/c/c89/c89-draft.html#3.5.4.2)
> **Semantics**
> If, in the declaration " T D1 ", D1 has the form
>
> D[ constant-expression<opt> ]
>
> and the type specified for ident in the declaration " T D " is "derived-declarator-type-list T",
> then the type specified for ident is " derived-declarator-type-list array of T".
> If the size is not present, the array type is an incomplete type.

# 정수 타입
정수 타입은 부호가 있는 정수 타입과 부호가 없는 정수 타입으로 나눠집니다. 

부호가 있는 정수 타입으로는 `signed char`, `short int`, `int`, `long int`가 있습니다. 
오른쪽으로 갈수록 같거나 더 넓은 범위의 정수를 표현할 수 있습니다. 

부호가 없는 정수 타입은 부호가 있는 정수 타입에서 `signed`를 `unsigned`로 바꾸거나, `unsigned`를 붙여서 만듭니다.
메모리 공간의 크기는 같지만 음이 아닌 정수만 나타내므로 더 큰 숫자까지 나타낼 수 있습니다.

#### 코드 예시:
```c
unsinged int i = 0; /* 변수 i에는 음이 아닌 값이 저장됩니다 */
```

#### 관련 C89 표준
[3.1.2.5 Types](https://port70.net/~nsz/c/c89/c89-draft.html#3.1.2.5)
> The type char, the signed and unsigned integer types, ... are collectively called integral types.
> The representations of integral types shall define values by use of a pure binary numeration system. ...
>
> There are four signed integer types, designated as signed char, short int, int, and long int.
> (The signed integer and other types may be designated in several additional ways, ...)
>
> An object declared as type signed char occupies the same amount of storage as a "plain" char object.
> A "plain" int object has the natural size suggested by the architecture of the execution environment. ...
> In the list of signed integer types above, the range of values of each type is a subrange of the values of the next type in the list.
>
> For each of the signed integer types, there is a corresponding (but different) unsigned integer type (designated with the keyword unsigned)
> that uses the same amount of storage (including sign information) ... The range of nonnegative values of a signed integer type is a
> subrange of the corresponding unsigned integer type, ...
>
> The type char, the signed and unsigned integer types, ... are collectively called the basic types.
> Even if the implementation defines two or more basic types to have the same representation, they are nevertheless different types.
>
> Integral and ... types are collectively called arithmetic types. ...

[3.5.2 Type specifiers](https://port70.net/~nsz/c/c89/c89-draft.html#3.5)
> **Constraints**
> Each list of type specifiers shall be one of the following sets;
> the type specifiers may occur in any order,
> possibly intermixed with the other declaration specifiers.
>
> signed char
>
> unsigned char
>
> short, signed short, short int, or signed short int
>
> unsigned short, or unsigned short int
>
> int, signed, signed int, or ...
>
> unsigned, or unsigned int
>
> long, signed long, long int, or signed long int
>
> unsigned long, or unsigned long int
>
> **Semantics**
> Each of the above comma-seperated lists designates the same type, ...

# 포인터 타입
포인터 타입은 함수, 변수 등의 주소를 저장할 수 있는 타입입니다.

`타입` `*` `이름` `;` 형태로 변수를 가리키는 포인터를 선언할 수 있습니다.

`타입` `(` `*` `이름` `)` `(` `)` 형태로 함수를 가리키는 포인터를 선언할 수 있습니다. 

#### 코드 예시:
```c
int *ptr_to_int; /* int 타입의 주소를 저장할 수 있는 포인터 타입의 변수 ptr_to_int를 선언합니다. */
int *f(); /* int 타입의 주소를 저장할 수 있는 포인터 타입이 반환타입인 함수 f를 선언합니다. */
int (*ptr_to_func)(); /* 반환타입이 int인 함수의 주소를 저장할 수 있는 포인터 타입의 변수 ptr_to_func을 선언합니다. */
```

#### 관련 C89 표준
[3.1.2.5 Types](https://port70.net/~nsz/c/c89/c89-draft.html#3.1.2.5)
> A pointer type may be derived from a function type, an object type, or an incomplete type, called the reference type.
> A pointer type describes an object whose value provides a reference to an entity of the referenced type.
> A pointer type derived from the referenced type T is sometimes called "pointer to T".
> The construction of a pointer type from a referenced type is called "pointer type derivation".
>
> Arithmetic types and pointer types are collectively called scalar types.
>
> Array, function, and pointer types are collectively called derived declarator types.
> A declarator type derivation from a type T is the construction of a derived declarator type from T
> by the application of an array, a function, or a pointer type derivation to T.

[3.5.4.1 Pointer declarators](https://port70.net/~nsz/c/c89/c89-draft.html#3.5.4.1)
> **Semantics**
> If, in the declaration " T D1 ", D1 has the form
>
> \* type-qualifier-list<opt> D
>
> and the type specified for ident in the declaration " T D " is "derived-declarator-type-list T",
> then the type specified for ident is "derived-declarator-type-list type-qualifier-list pointer to T".
> For each type qualifier in the list, ident is a so-qualified pointer.

