more examples here...

* Lambdas vs Procs Returning Behavior

```
def proc_math
  Proc.new { return 1 + 1 }.call
  return 2 + 2
end
 
def lambda_math
  lambda { return 1 + 1 }.call
  return 2 + 2
end
 
proc_math # => 2  
lambda_math # => 4
```
As you can see proc_math hits the return statement inside the Proc and returns the value of 2. In contrast, lambda_math skips the return statement and evaluates 2 + 2 instead.
