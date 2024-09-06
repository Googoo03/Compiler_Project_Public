# CS152_Project
A custom compiler developed in CS 152 by Nicholas Karalis, Garrett Greenup, and Alessandro Bombarda.

## Description
This compiler is a basic demonstration of our skills with parsing, syntactic analysis, and intermediate code generation using the Yacc and Bison compiler libraries. The language supported the various operators listed below as well as many logical features found in mainstream programming languages.

### Example Program
Below is one of our example files, Logic.agn, that demonstrates basic programming logic at play. Additionally, any and all files with our programming language have the extension .agn.
```
// Example program demonstrating if-else statements

define main as() -> {
    int x;
    int y;
    int z;

    
    x = 10;
    y = 5;
    if x or y {
        z = 0;
    } else {
        z = 1;
    }

    // Should print out '0'.
    write(z);

    if x and z {
		write(x and z); 
	}
	else {
		write(x);
	}
	// Should print out '10' (x)

    write(z and y); // Should print out '0'
}
```

This program outputs the following intermediate code after being parsed and ran through our lexer.

```
func main
. x
. y
. z
= x, 10
= y, 5
. _tmp_1
|| _tmp_1, x, y
?:= start_if_1, _tmp_1
:= start_else_1
: start_if_1
= z, 0
:= end_else_2
: start_else_1
= z, 1
: end_else_2
.> z
. _tmp_2
&& _tmp_2, x, z
?:= start_if_2, _tmp_2
:= start_else_3
: start_if_2
. _tmp_3
&& _tmp_3, x, z
.> _tmp_3
:= end_else_4
: start_else_3
.> x
: end_else_4
. _tmp_4
&& _tmp_4, z, y
.> _tmp_4
endfunc
```

### Language Features
Below is a list of operators and commands that our language supports. Additional examples of these can be found in our [Examples](Examples) folder.

| Language Feature      | Code Example |
|-----------------------|--------------|
| Variable Declaration  | int x;       |
| Add                   | x + y        |
| Sub                   | x - y        |
| Multiply              | x * y        |
| Divide                | x / y        |
| Modulus               | x % y        |
| Less Than             | x < y        |
| Less Than Equal       | x <= y       |
| Equality              | x == y       |
| Not Equality          | x != y       |
| Greater Than          | x > y        |
| Greater Than Equal    | x >= y       |
| Logical or            | x or y       |
| Logical and           | x and y      |
| Logical xor           | x xor y      |
| Write                 | write(x)     |
| Read                  | read(x)      |
| Arrays                | int [8] array|
| Comments              | // This is a comment|

### Table of Symbols

|Symbol                | Token Name   |
|----------------------|--------------|
|define                | Define       |
|as					   | As           |
|return                | Return       |
|int                   | Int          |
|write                 | Write        |
|read                  | Read         |
|while                 | While        |
|if                    | If           |
|else                  | Else         |
|break                 | Break        |
|continue              | Continue     |
|and                   | Logical and  |
|or                    | Logical or   |
|xor                   | Logical xor  |
|(                     | LeftParen    |
|)                     | RightParen   |
|{                     | LeftCurly    |
|}                     | RightCurly   |
|[                     | LeftBracket  |
|]                     | RightBracket |
|->                    | Arrow        |			
|,                     | Comma        |
|;                     | Semicolon    |
|+                     | Plus         |
|-                     | Minus		  |
|*                     | Multiply     |
|/                     | Divide       |
|%                     | Modulus      |
|=                     | Assign       |
|<                     | Less         |
|<=                    | LessEqual    |
|>                     | Greater      |
|>=                    | GreaterEqual |
|==                    | Equality     |
|!=                    | NotEqual     |
|!                     | Not          |
|variable_name         | Ident        |
|10311517              | Num          |

### Comments

Comments can be single line comments starting with `//`. For example:

```
int x; //This is a variable declaration.
```
