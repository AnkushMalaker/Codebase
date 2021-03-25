# Array manipulation and stuff

## Initilizing  
Vector can be initialized as such:  
```x = Array{T}(type, length)```  
or  
```a = Vector{Float64}()```  
This creates an unitialized array. To create an initialized array, use:  
```myArray = [1,2,3]```  
or  
```x = zeros(Float64, 10)```  
### Accessing array elemtns
This can be done via  
```a1[5]``` or ```a1[end]``` for the last elemtn

Accessign a range from the array:  
```a[0:7]``` or ```a[3, end]```
To access particular elements, we can do:  
``` c1[[1, 3, 5]]```  
to access the 1st, 2nd and 4th element (Note the double brackets). 



## Adding values  
### Push and append
Add indivisual elements to an array with  
```push!(a, 1.0)```  
or an array of elements using append:  
```append!(x, [1.0, 2.0])``` 
Both these methods add elements are the end of the array.  
To add in the beginning, use:  
```pushfirst!(array1, "welcome")```   

or to add in a specified position, use:  
``` splice!(array1, 3:4, "abc")```  

## Adding elements in a 2d array  
 
```Array3 = [Array1; Array2]```  
This is extremely inefficient due to a varity of reasons, so using it in a loop is extremely inefficient (Something to do with vcat or hcat being called and a new array being created each time.) Better allocate memory before hand and cut from there.  

## Deleting elements  
The pop method can delete the last element:  
```pop!(a1)```  

For deleting from front,  
```popfirst!(a1)```  
To delete a specific element:  
```splice!(a1, 4)```  
Delete a range of elements:  
```deleteat!(a1, 2:4)```  
Delete all elements:  
```empty!(a1)```  

## Array of arrays  
This is somehow extremely confusing for me, so lest I forget it, to create an array of arrays, we do:  
``` a = Array[ [1,2], [3,4]]```  
which will result in a 2x2 array which will be Array{Array{T, N}, 1}. If we want a vector of vectors for example, we may do:  
```a = Vector{Int}[[1,2], [3,4]]```   

```Array{Array{Float64,1},2}(undef, 10,10)```     #creates a two-dimensional array, ten rows and ten columns where each element is an array of type Float64
```Array{Array{Float64, 2},1}(undef,10)``` #creates a one-dimensional array of length ten, where each element is a two-dimensional array of type Float64

## Broadcasting 
Broadcasts a singleton element over a size to add to multiple elements. Example: Adding a vector to each column of a matrix.
```broadcast(+, a, A)```   

Good resource for a quick look and important methods: 
[Geeksforgeeks article](https://www.geeksforgeeks.org/arrays-in-julia/#:~:text=Adding%20elements%20to%20an%20Array&text=Julia%20allows%20adding%20new%20elements,function.)  

Ofc, the [docs](https://docs.julialang.org/en/v1/manual/arrays/) are the most expansive and elaborate.