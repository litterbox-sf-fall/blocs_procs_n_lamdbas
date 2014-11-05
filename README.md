#Procs, Blocks, and Lamdas

##Intro
In javascript we were creating functions which we could pass in as arguments. In ruby we can do that as well.

```
def one
	return 1
end
```
Let say we want to pass in the above function `one` to another function.
If we say `x = one` x will not be equal to a method, but rather the value 1. `x.class => Fixnum < Integer`

Clearly we need another way to do this. As a result we have to find a way to pass in a block a code. What is a block though?

## Block Examples

```
[1,2,3].each { |x| puts x*2 }   # block is in between the curly braces

[1,2,3].each do |x|
  puts x*2                    # block is everything between the do and end
end
```

##Blocks vs Procs
* Exactly the same, except...
* Blocks can't be stored in variables; however, procs can!

##Procs Examples

```
fact = Proc.new{|n| n * n }
multiply = Proc.new {|x, y| x * y }
```

```
p fact.call(3)               #=>This will invoke ‘fact’ Proc and return 9
p multiply.call(4, 3)           #=>This will invoke ‘multiply’ Proc and return 12
```

```
multiply.call(4, 3)
multiply[4, 3]
```
   
```        
p = Proc.new { |x| puts x*2 }
[1,2,3].each(&p)              # The '&' tells ruby to turn the proc into a block 

proc = Proc.new { puts "Hello World" }
proc.call                     # The body of the Proc object gets executed when called
```

###Extra Credit

##Procs vs Lambdas
* Lamda's are a different 'flavor' of a vanilla proc
* Lambdas check the number of arguments, while procs do not
	* Procs will drop any extra arguments; lambda will throw an error
* Lambdas and procs treat the ‘return’ keyword differently
	* ‘return’ inside of a lambda triggers the code right outside of the lambda code
	* ‘return’ inside of a proc triggers the code outside of the method where the proc is being executed

## Lambda Examples 
```           
lam = lambda { |x| puts x*2 }
[1,2,3].each(&lam)

lam = lambda { puts "Hello World" }
lam.call
```
	
##Closures?
* A function passed into another function
