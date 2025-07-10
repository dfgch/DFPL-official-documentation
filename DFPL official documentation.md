## DFPL - official documentation!
> dfgch programming language - The DFPL language is used exclusively for programming my BizMut2.0 processor - **it is not a high-level language**, it is not even particularly advanced, but its idea is simple: it is easy to program the BizMut2.0 processor!


# Content
__Tools__ ....................................................................................................................................................................................................................................................................................
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[BizMut2.0 conductor]()\
__DFPL overview__ .................................................................................................................................................................................................................................................................
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Files](#files)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[.INI block](#ini-block)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[.Code block](#code-block)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Prefixes](#prefixes)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Variables](#variables)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Tags](#tags)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[DFPL optymalization](#dfpl-optymalization)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[DFPL build-in functions]()\
__DFPL commands__ .............................................................................................................................................................................................................................................................
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Import](#import)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Export](#export)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__operating on variables__\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Addition](#addition)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Subtraction](#subtraction)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Multiplication](#multiplication)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Division](#division) (and mod)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Exponentiation](#exponentiation)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[When](#when)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Repeat](#repeat)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Own functions]\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Pause]\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Plot]\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Update]\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Reset]\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Awiat]\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;__Operating on list__\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Operating on a string]\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[len]\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Dv]\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[Write]

## BM2.0 Conductor
(soon)

## Files
DFPL compiler files: soon\
Files are best opened in the Visual Studio Code and sorted in the appropriate way:
Code -> DFPL compiler -> compiler output -> BizMut2.0 assembler -> machinecode -> schematic generator.

# INI block
````
ini:
    offset: 0
    #MINIMAL RAM size in cpu: 580B
    #MINIMAL ROM size in cpu: 6KiB
    ram_for_program: 500
    output_standard_port: 0
    input_standard_port: 0
    display_X_port: 7
    display_Y_port and plot: 6
    display_update_port: 4
    display_reset_port: 5
````
__The "Code.txt" file must contain ini and underneath the ini block, code ** this is required **__\

When you start programming the offset point is crucial because it is the point on the page where the program starts and in BizMut2.0 you will find the offset here:\
![e](https://cdn.discordapp.com/attachments/1091278557591908383/1392888640841191495/Minecraft__1.18.2_-_Tryb_jednoosobowy_10.07.2025_17_21_43.png?ex=68712c22&is=686fdaa2&hm=8e037d893be115f09137b9e71995274c406b305f69bb3179b0838a875a85fe08&)\
\
The point "ram for program" is quite crucial because this
value tells the DFPL compiler how many ram cells it can
use in the processor, it means that in the DFPL language
you can create 300 variables and lists that have a
maximum of 200 elements together.\
\
Output_standard_port and imput_standard_port points tell where the processor should redirect the value from the variable in the program when you use import and export.\
\
You can also configure display ports for plot pixel command in DFPL.

# Code block
```
ini:
    offset: 0
    #MINIMAL RAM size in cpu: 580B
    #MINIMAL ROM size in cpu: 6KiB
    ram_for_program: 500
    output_standard_port: 0
    input_standard_port: 0
    display_X_port: 7
    display_Y_port and plot: 6
    display_update_port: 4
    display_reset_port: 5
code:
    program
    program
    program
    program
```
In the code block you write the DFPL program code\
__The offset settings is imporant__

# Prefixes
You can add comments to the code like this: (# or ; or :)
```
Code:
    #Load variables:
    A = 5
    B = 3
```
You can also make holes in the code:
```
Code:
    A = 10
    B = 2
    C = 0

    C = A + B
```

# Variables
"variable_name = value" must appear in the code to create a variable!. The number of variables depends [on the value at an a ini block](#ini-block)\
variables can't be named 1, 2, 3......
```
Code:
    A = 5
    B = 10
    C = 0
    C = A + B
```

# Tags
For example .tag we define where our function is located in the program.
```
Code:
    A = 5 .load_values
    B = 5
    C = 0




    teleport to function .load_values
    C = A + B
```

# DFPL optymalization
DFPL can remove unused variables in code and save RAM.

# Export
The Export command in DFPL is used to export a variable
to a [standard port](#ini-block) which you can set here.
```
Code:
    #Creating variable
    A = 5

    #Export variable A to standard port
    export A
```

# Import
The Import command in DFPL is used to read the standard port and load it into a variable.
```
Code:
    #Creating valiable
    A = 0

    #loadgin standard port into variable
    import A
```

# Operating on variables
To start with, each variable must be defined, otherwise
the DFPL compiler will return an error!
```
Code:
    #Creating a variable
    A = 0
```
There are no data types or any types of variables.
You can also do this:
```
Code:
    #Creating a variables
    A = 0
    B = 5

    #move
    A = B
```

# Addition
You can operate on variables and values.
```
Code:
    #Creating a variables
    A = 10
    B = 3
    C = 0

    #Addition
    C = A + B
```

or:
```
Code:
    #Creating a variables:
    A = 10
    B = 0

    #Addition
    B = A = 10
```
# Subtraction
```
Code:
    #Creating a variables
    A = 10
    B = 3
    C = 0

    #Subtraction
    C = A - B
```
or:
```
Code:
    #Creating a variables
    A = 10
    B = 3

    #Subtraction
    B = A - 5
```
# Multiplication
The multiplication operation uses the built-in DFPL function - the DFPL compiler creates the multiplication code itself.
```
Code:
    #Creating a variables
    A = 10
    B = 3
    C = 0

    #Multiplication
    C = A * B
```
```
Code:
    #Creating a variables
    A = 10
    B = 0

    #Multiplication
    B = A * 30
```
# Division
Just like with multiplication, the DFPL compiler creates division functions itself.
```
Code:
    #Creating a variables
    A = 10
    B = 2
    C = 0

    #Division
    C = A / B
```
```
Code:
    #Creating a variables
    A = 10
    B = 0

    #Division
    B = A / 2
```
You can also bend the remainder from division.
```
Code:
    #Creating a variables
    A = 10
    B = 2
    C = 0

    #mod
    C = A // B
```
```
Code:
    #Creating a variables
    A = 10
    B = 0

    #mod
    B = A // 2
```
# Exponentiation
DFPL allows you to further exponentiate variables.
```
Code:
    #Creating a variables
    A = 10
    B = 2
    C = 0

    #Exponentiation
    C = A ^ B
```
```
Code:
    #Creating a variables
    A = 10
    B = 0

    #Exponentiation
    B = A ^ 2
```

# When
The when operation executes the code described in {} using a condition - if the condition is true, the code will be executed, if not, it will be skipped.\
__Conditions you can use: =?, !=?, >?, <?__\
Examples in programs:
```
Code:
    a = 5
    when a >? 5 {
        export a
    }
```
```
Code:
    a = 5
    b = 19
    when a =? b {
        a = 19
    }
```
or:
```
Code:
    a = 3
    when a > 0 {
        when a < 10 {
            export a
            a = a + 1
        }
    }
```

# Repeat
The Repeat operation allows you to do conditional loops and period loops.\
The arguments supplied to this operation are not modified.
```
Code:
    a = 0
    loops = 10

    repeat loops {
        a = a + 1
    }
```
```
Code:
    a = 0

    repeat 10 {
        a = a + 1
    }
```
```
Code:
    a = 0

    repeat until a =? 10 {
        a = a + 1
    }
```
or:
```
Code:
    a = 0
    loops = 10

    repeat loops {
        repeat 10 {
            export a
            a = a + 1
        }
    }
```


















































































































