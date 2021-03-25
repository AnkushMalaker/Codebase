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
```a1 = [1,2,3,4,5]```  

Note: If there's multiple types in it (like integer and float), it will be implicitely converted.  

Array can also be of functions.  

If we have an array like  
``` a1 = [1,2,3,4,"Hello"]```  
We will get an array of type "Any"  

We can force the array to be a type by:  
``` a1 = Float64[1,2,3,4]```  
We will get an array of type "Any"  

2D arrays made by splitting array elements using ";"
For exapmle:  
```a1 = [1, 2; 3, 4]```  

Array of random values can be made using rand(10), which will give a random array of type Float64

### Ranges
Made using ```collect(start, interval, end)```

Reverses can be similarly made:   
``` collect(100:-20:0)```

### Accessing array elemtns
This can be done via  
```a1[5]``` or ```a1[end]``` for the last elemtn

Accessign a range from the array:  
```a[0:7]``` or ```a[3, end]```
To access particular elements, we can do:  
``` c1[[1, 3, 5]]```  
to access the 1st, 2nd and 4th element (Note the double brackets). 

### Tuples
Immutable. Initialized in a similar way like arrays but with ```()``` instead of ```[]```.  
We can create named tuples as well:  
```marks = (Science = (90, 100), Maths = (30, 100))```  

Tuples can be merged using ```merge(tuple1, tuple2)```

### Dictionary 
Defining dictionary:  
```Cars = Dict("car1" => 200, "cat2" => 300)```  
or 
```Cars = Dict(:Car1 => 200, :Car2=> 300)```  
(Second method creates keys as symbols instead of strings)   

Accessing dictionary:  
Cars["car1"]

#### Check if dict has a key
```haskey(Cars, "car1")```  

#### Delete keys 
```delete!(cars, "car1")```

#### Get keys
```keys(Cars)```

#### Get values
```values(Cars)```

Merging is done with the same as tuples

### Sets
Sets are unordered and don't have duplicate elements. Initialization:  
``` brands = Set(['Greedbook', 'Nonke', 'Yeet'])```  

Check if val exists in the set:  
```in("Yeet", brands)```   

Has operations such as: ```union```, ```intersect```, ```setdiff```   

Also operations like ```push``` etc


### Date and time

#### Data types
-  Dates.Time
-  Dates.Date
-  Dates.Datetime

These need to be imported by:  
```using Dates```  

#### Current date and time 
```now()``` # has date AND time  
```today()``` # has todays date in yyyymmdd format  
```now(UTC)``` # Converts timezone  
```year(birthdate)``` # Extracts the date  
etc.

### Conditional Statements
Simple condition:  
```a > 10 ? "yes" : "no"```  

#### Logical operators
OR ```||```, AND ```&&```  

#### If conditions 
Same as every programming language in existance. (Don't take this literally please.)

### Loops
```
for i in ["aloo", "gobi", "mattar"]
	print(i, " "")
end
```  
This is dynamically typed, ie, i will take the dataType of what is in the list.  

Similarly can be used to loop through each char of a string.  

#### Looping through range  
```
for i in 1:5
	print(i)
end
```  

### Printing numbers between lines
```print("Your total sum is: $(j)")```  
where j is the variable to be printed.  

#### While loops 
Also same as literally every other programming language.  

### Comprehensions  
```[i for i in 1:10]```  
or do operations on the elements as:  
```[i^2 for i in 1:10]```  
to do if statements within the comprehention:  
```[x for x in 1:10 i x%2==0]```

or create a two dimentional array like:  
```[(x,y) for x in 1:3, y in 1:2)]```  

### Strings
Length can be found using  
```length(s1)```  
but ```lastindex(s1)``` has less computation and returns the same.  

-Strings can be concatednated using the ```*``` symbol.  
-Strings can be multiplied using the ```^``` symbol.  
-Strings can be split using ```split(s1, "<delimiter>")```  
-Strings can be parsed using ```parse(integer64, "100")```  

### Functions
Generic function can be created using:  
```f(x) = x + x```  
and called like  
```f(2)``` which outputs 4.  

or named fucntions like  
```
function multiply(x, y)
	return x*y
end
```

#### Default values can be supplied for variables using ```=``` in the definition  
For example:  
```
function multiply(x=5, y)
	return x*y
end
```
