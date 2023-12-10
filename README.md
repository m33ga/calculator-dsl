# Simple Calculator DSL
## The Task

In this task, you will create your own simple calculator Domain-Specific Language (DSL), similar
to the example provided during our class. You have the freedom to make choices in the following aspects:

1. Syntax: You can design a syntax of your choice, which can be as unconventional as languages like Brainfuck, as long as it adheres to the constraints specified in the constraints section.
2. Grammar: You have the freedom to define the grammar for your DSL as you see fit.
3. External Libraries: You are allowed to use external libraries to assist in your implementation, but they should not directly solve your problem. 
4. Tree Parsing Algorithm: You are free to choose any parsing algorithm you prefer.


Constraints:

1.  You must implement a lexer, a parser, and an interpreter for your DSL.
2.  Your interpreter should parse the tree generated by the parser, not just the tokens produced by the lexer.
3.  Variable Declaration: Each variable declaration must specify its data type explicitly(e.g., ’var int x’, ’float y = 9.8’).
4.  Arithmetic Operations: Your DSL must support basic arithmetic operations, such as addition, subtraction, multiplication, and division.
5.  Control Structures: Implement at least one control structure, such as conditionals (e.g., if statements) and one loop (e.g., for or while loops) in your DSL.
6.  Error Handling: Your DSL should provide clear error messages for syntax and runtime errors, making it user-friendly.
7. Interactive Mode: Implement an interactive mode where users can enter DSL code line by line(you can use external text file for code input).
8. Modular Design: Organize your DSL implementation into separate modules or components for the lexer, parser, and interpreter to maintain a clean and maintainable codebase.

## Syntax rules:

```
program = "program:"
        ["int:" identifier {"," identifier} ";"]
        ["double:" identifier {"," identifier} ";"]
        statement

statement = identifier "=" expression
            | "print:" identifier
            | "{" statement {";" statement } "}"
            | "if:" condition "then:" statement ["else:" statement]
            | "while:" condition "do:" statement

condition = expression ("=="|"!="|"<"|"<="|">"|">=") expression

expression = ["+"|"-"] term {("+"|"-") term}

term = factor {("*"|"/") factor}

factor = identifier | number | "(" expression ")"
```

Keyword meanings:

         program: -  Marks the beginning of the program
         int: - Integer variable declaration
         double: - Double variable declaration
         while: - While loop condition follows 
         do: - Statement block follows which will be executed as long as the while condition is true 
         if: - If statement condition
         then: - Statement block follows which will be executed once if the condition is true 
         else: - Statement block follows which will be executed once if the condition is false 
         print: - Prints value of a variable and goes to a new line




## Instructions on how to write a program

1.  Each program starts with the keyword "program:"
2.  All integer variables (if any) are declared first, using the "int:" keyword. Variable names are separated by commas and the line is ended by semicolon.
3.  All double variables (if any) are declared next, using the "double:" keyword. Variable names are separated by commas and the line is ended by semicolon.
4.  Next follows the block of statements. The beginning of the block is marked by "\{" and the end is marked by "\}"
5. Each statement inside a block is followed by semicolon except the last statement inside the block.
6. A statement block may contain: assignment statements, print statements, if statements and while statements.
7. If statements start with the keyword "if:" and are followed by a condition.
8. The condition is written without parenthesis. Condition consists of a comparison between two expressions. The expressions may contain any order of valid mathematical operations(addition, subtraction, multiplication and division). Parenthesized expressions are also allowed.
9. If statements have to contain a block of code written between curly braces after the "then:" keyword. If the "else:" keyword is added, a block of code has to follow it written between curly braces. A semicolon follows the statement, unless it is the last statement.
10. While statements start with the "while:" keyword. They are followed by a condition written without parenthesis. The "do:" keyword comes next, followed by a block of code written between curly braces "\{", "\}". A semicolon follows the statement, unless it is the last statement.
11. Print statement starts with the "print:" keyword. It accepts ONLY ONE VARIABLE NAME, the value of which will be printed. A semicolon follows the statement, unless it is the last statement.
