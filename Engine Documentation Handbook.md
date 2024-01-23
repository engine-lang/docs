# بسم الله الرحمن الرحيم
اللَّهُمَّ انْفَعْنِي بِمَا عَلَّمْتَنِي، وَعَلِّمْنِي مَا يَنْفَعُنِي، وَزِدْنِي عِلْمًا


# Introduction
This is the documentation for the engine programming language and it's ecosystem.


# Developing

## Dependencies
* Rust Programming Language


## Installing
First clone the repo
```bash
git clone git@github.com:engine-lang/engine.git
```

Then create engine file
```bash
touch test.en
```
and put this code
```ex
string variable_1 = "hello"
print(variable_1)

string variable_2 = ", world!!!!"
print(variable_2)
```


## ## Run engine as Interpreter
You can run engine as an interpreter on the file by just running
```bash
cargo run "test.en"
```

it should print
```bash
hello, world!!!!
```


## ## Run engine as a Compiler
You can run engine as a compiler which will generate an executable.

```bash
cargo run "test.en" -e
```

it will generate an executable file called `test`, and to run it

```bash
./test
```

it should print
```bash
hello, world!!!!
```


## Generate byte Code
You can generate a byte code like this
```bash
cargo run "test.en" -b
```

it will generate a file called `test.en.byte` in this format
```ex
0:EngineByteCode:v0.1.0
1:Assign:string:"temp_stack1_variable_1":"hello"
2:Assign:string:"stack1_variable_variable_1":""
3:Convert:string:"stack1_variable_variable_1":"temp_stack1_variable_1"
4:Print:"stack1_variable_variable_1"
5:Assign:string:"temp_stack1_variable_2":", world!!!!"
6:Assign:string:"stack1_variable_variable_2":""
7:Convert:string:"stack1_variable_variable_2":"temp_stack1_variable_2"
8:Print:"stack1_variable_variable_2"
9:End:
```

you can then use it to your specific cases, or you can run it using engine vm


## Run engine as VM(Virtual Machine)
To execute the engine byte code file, you can run
```bash
cargo run "test.en.byte" --vm
```
it will interprete the file


__

# # Comments

## ## Single line comment

```ex
# This is a single line comment
```

## ## Multi line comment
```ex
/*
    This is
    multi line
    comment
*/
```

__


# # Define Variables

## ## Bool

To define boolean variable

```ex
bool variable = True
bool variable_1 = False
bool variable_2 = False || True
bool variable_3 = False && True
bool variable_4 = 5 + 4 > 3 + 7 && 5 % 2 == 1
```

## ## Int
To define Integer variable

```ex
int variable_0 = 5
int variable_1 = 6 + 5 - 7 * 7 / 2 + (
    5 - variable_0 * ( 6 % 2 )
)

variable_1 += 5
variable_1 -= 5
variable_1 *= 5
variable_1 /= 5
variable_1 %= 5
```

## ## Double
To define Double variable

```ex
double variable = 6.2 + 8
double variable_2 = 0.1 - 0.4
```

## ## Char
To define Character variable

```ex
char variable = 'H'
char variable_1 = "h"
```

## ## String
To define String variable

```ex
string variable = "Hello World"
string variable_1 = 'Hello world!!'
string variable_2 = "Hello" + " World" + ',' + ' Dude!!!'
```


## ## Define variable without writing the type
You can define variables without writing the variable type like that.

```ex
var new_variable = True
```
or directly
```ex
new_variable = True
```

the language will try to infer the type of the variable then define new variable
based on the infered type, so the new variable will be of type boolean.


## ## A Note
take a special note that if you define character like this
```ex
new_variable = 'H'
```
the language will consider it as string.

__

New line is the line terminator for the statement (like simicolon in c and c++)

# # Precedence
This is the precedence of the operators

1. ( True, False, Int Number, Double Number, Variable, Character, String, Open Parenthese - Close Parenthese - () )
2. ( *, /, % )
3. (  +, - )
4. ( <, <=, >, >= )
5. ( ==, != )
6. ( && )
7. ( || )


__


# # Print Statement
To print a variable you can do
```ex
bool variable = False
print(variable)
```

or you can print a statement directly
```ex
print("Hello, " + "World !!!")
```


__


# # Input Statement

To get an input from the console

```ex
var line = input()
```

input will be of type `String`.

to get input of another types
```ex
var line1 = input() as bool
var line2 = input() as int
var line3 = input() as double
var line4 = input() as char
var line5 = input() as string
```

this will get the input from console and convert it to the type you specified.

you can also use it in an expression like this.
```ex
var x = 5 + input() as int + 7
print(x)
```

it take the input and assign the result sum value to `x` variable.


__


# # If Statement

## ## Syntax
You can make an if statement in this syntax

```ex
if condition {
    # Statements
}
else if condition {
    # Statements
}
else {
    # Statement
}
```

### ### Examples
```ex
x = input() as int
if x > 5 {
    print("X is Greater than 5")
}
else if x < 5{
    print("X is less than 5")
}
else{
    print("X is equal to 5")
}
```

## ## Nested If
you can make nested if
```ex
x = input() as int
if x > 5{
    if x < 10{
        print("X is Greater than 5 and less than 10")
    }
    else{
        print("X is Greater than 10")
    }
}
else if x < 5{
    print("X is less than 5")
}
else{
    print("X is equal to 5")
}

```


__


# # For Loop

## ## Syntax
you can create a for loop statement like this

```ex
for i in (start, end, step){
    # Statements
}
```

Or you can skip any element like this
```ex
for i in (, end, step){
    # Statements
}
```
This will generate loop starting from `0`

Or
```ex
for i in (start, , step){
    # Statements
}
```
This will make an infinity loop as we didn't define `end`

Or
```ex
for i in (start, end, ){
    # Statements
}
```
This will loop forever as we didn't increament the step counter


## ## Examples
```ex
for i in (0, 10, 1){
    print(i)
    print("\n")
}
```

__


## ## Break Statement
You can define break statement inside for loop statement like this

```ex
start = 0
end = 10
step = 1
for i in (start, end, step){
    if x > 5{
        break
    }
}
```

## ## Continue Statement
You can define continue statement inside for loop statement like this

```ex
start = 0
end = 10
step = 1
for i in (start, end, step){
    if x > 5{
        continue
    }
    print("Hello World\n")
}
```

__


# # Byte Code

## ## Introduction
This is the byte code instructions that will be generated if you want to compile the code into byte code.


____


## ## `EngineByteCode` Instruction
This is the first instruction in the file

`LINE:EngineByteCode:v0.1.0`
* `LINE` => is the current instruction line, it will start from `0`
* `EngineByteCode` => Instruction Type
* `v0.1.0` => Current version

____


## ## `Assign` Instruction
This instruction is used to create new variable then assign it with value.

`LINE:Assign:VariableType:"VariableName":VariableValue`
* `LINE` => is the current instruction line
* `Assign` => is the instruction Type
* `VariableType` => is the Variable type for ex: (bool, int, double, character, string)
* `"VariableName"` => Variable Name with double quotes
* `VariableValue` => The value for the variable for ex: (True, False, 5, 'H', "Hello")

### ### Exampls
```ex
5:Assign:bool:"variable_1":True
6:Assign:bool:"variable_2":False
7:Assign:int:"variable_3":5
8:Assign:double:"variable_4":5.2
9:Assign:char:"variable_5":'H'
10:Assign:string:"variable_6":"Hello, World!"
```

____


## ## `Convert` Instruction
This instruction is used to convert the value from type to another.

`LINE:Convert:ConvertToType:"AsssignToVariableName":"FromVariableName"`
* `LINE` => is the current instruction line
* `Convert` => Instruction Type
* `ConvertToType` => This is the convert to type for ex: (bool, int, double, character, string)
* `"AsssignToVariableName"` => Variable name which the converted value will be put in it.
* `"FromVariableName"` => Variable name which will have the value which needs to be converted.


### ### Examples
```ex
5:Convert:bool:"Variable2":"Variable1"
6:Convert:double:"Variable3":"Variable4"
7:Convert:char:"Variable5":"Variable6"
```

____


## ## `Operation` Instruction
This is the operations instruction

`LINE:Operation:OperationType:"AssignToVariableName":"LeftVariableName":"RightVariableName"`
* `LINE` => is the current instruction line
* `Operation` => Instruction Type
* `OperationType` => Operation Type (
    Plus, Minus, Mul, Div, Mod,
    And, Or,
    GreaterThan, GreaterThanOrEqual, LessThan, LessThanOrEqual,
    Equal, NotEqual)
* `"AssignToVariableName"` => The variable name which the final value will be assigned to it.
* `"LeftVariableName"` => the first variable
* `"RightVariableName"` =>  the second variable


### ### Examples
```ex
6:Operation:Plus:"Variable3":"Variable2":"Variable1"
7:Operation:And:"Variable5":"Variable4":"Variable3"
```

____


## ## `Print` Instruction
This is the print instruction

`LINE:Print:"VariableName"`
* `LINE` => is the current instruction line
* `Print` => Instruction Type
* `"VariableName"` => The variable name to print

### ### Examples
```ex
5:Print:"Variable"
```

____


## ## `Input` Instruction
This is the input instruction.

`LINE:Input:"VariableName"`
* `LINE` => is the current instruction line
* `Input` => Instruction Type
* `"VariableName"` => The variable name to put the input value in it.


### ### Examples
```ex
18:Input:"temp_stack1_variable_7"
```

____


## ## `If` Instruction
This is the if control flow instruction.

`LINE:If:"VariableName":GoToLINE`
* `LINE` => is the current instruction line
* `If` => Instruction Type
* `"VariableName"` => Variable name to compare it's value, it's value will be True or False.
* `GoToLINE` => The Instruction line to go to if the condition for if statement is False, (`"VariableName"` value is False)


### ### Examples
```ex
227:If:"temp_stack2_variable_108":234
```

____


## ## `GoTo` Instruction
This is the Go to instruction, which is used to just go for another line.

`LINE:GoTo:GoToLine`
* `LINE` => is the current instruction line
* `GoTo` => Instruction Type
* `GoToLine` => The line number to go to it.

### ### Examples
```ex
233:GoTo:246
```

____


## ## `End` Instruction
This is the last byte code instruction to be generated

`LINE:End:`
* `LINE` => is the current instruction line
* `End` => Instruction Type


### ### Examples
```ex
130:End:
```
