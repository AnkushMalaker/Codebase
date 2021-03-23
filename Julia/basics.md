# Julia basic statements/notes

### Printing
print("hello world")

### Clear screen
Ctrl + L

### Interrult 
ctrl + c

### Help files
#### Normal help
Press ```?```
Enter command

#### Package related help
Press ```]```

### List all functions/methods with input
Two tabs after entering something (Kind of like tab completion)

### Install packages by doing 
pkg.add("IJulia")

### Variable declaration
Variable declaration is python-like for example: 
```loan_amout = 300```

This can be a string using " ", integer64 by putting integer, or float64 by putting float num

#### Variable names can't start with numbers. and can't contain special symbols in the name
### Check variable type
```typeof()```

### Commenting
Use \# for commenting 

### Arrays
Initialize it like:
``` a1 = [1,2,3,4,5]```

Note: If there's multiple types in it (like integer and float), it will be implicitely converted.

Array can also be of functions

if we have an array like 
``` a1 = [1,2,3,4,"Hello"]```
We will get an array of type "Any"

We can force the array to be a type by:
``` a1 = Float64[1,2,3,4]```
We will get an array of type "Any"


2D arrays made by splitting array elements using ";"

Array of random values can be made using rand(10), which will give a random array of type Float64

### Ranges
Made using ```collect(start, interval, end)```

Reverses can be similarly made:
``` collect(100:-20:0)```


