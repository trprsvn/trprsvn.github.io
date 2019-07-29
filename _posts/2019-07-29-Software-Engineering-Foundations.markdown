---
layout: post
---
I will recap some parts of Software engineering foundations in [App Academy][app_academy].
## Differences Between Argument and Parameter

Yes there might be confusion about what is parameter and what is argument. We may
either use them interchangeably. I believe there is a super memorable analogy from the one of the 
comments in [stackoverflow question][stackoverflow_question] which explains the difference.
> You can think of the  **p**arameter as a **p**arking space and the **a**rgument as an **a**utomobile." <br>
– Michiel van Oosterhout 

*Here is a simple example:*
```rb
# Here name is parameter
def greeter(name=nil)
  name ||= "Stranger"
  puts "Hello #{name}!"
end

# and here the name is actually used as data and argument
logged_in_user = "John Doe"
greeter(logged_in_user) # => "Hello John Doe!"
```

## Splat Operator

Think about it opening a package. 
If we accept many unknown number of parameters. `*` will be in our assistance.
```rb
def my_sum(num_1, num_2)
  p num_1 + num_2
end

my_sum(23, 44, 45) # => ArgumentError: wrong number of arguments (given 3, expected 2)

# splat * here will be useful

def my_sum(*nums)
  p nums.sum
end
```
if you looked closely we used nums parameter as an array. In deed we can * operator
can convert lists to array and vice versa.

## Algorithms and Bubble Sort

in order to find a book in a library we look for the genre, title, author etc.
and by doing so quickly find the book we are searching. Imagine library keeper
did not organize the books and they were mixed. It will take way to more time to find 
anything. And in programming it is the same. We use sorting algorithms to sort data.
(Algorithm is sequence of actions to take.) Bubble sort is one of the algorithms 
to sort things out. If we wanted to find a maximum
number it will be much easier to find a maximum on a sorted array. One of the sorting 
algorithm we inspect is bubble sort. So how a bubble sorting is working. First we
 compare the first number in an array with the immediate element next to it. If it is
larger than the current number it stays where it is. And go to next number in the
array. If the number is bigger than the next element they switch places. So by the
 end of the one iteration we have either full sorted array else we continue to 
 the same process over again.

*Implementation*

```rb
def bubble_sort(arr)
  sorted = false
  while !sorted
    sorted = true
    (0...arr.length-1).each do |i|
      if arr[i]>arr[i+1]
        arr[i], arr[i+1] = arr[i+1], arr[i]
        sorted = false
      end
    end
  end
  arr
end

puts bubble_sort([1,4,2,3]) # => [1,2,3,4]
```

## Scope and Value vs Reference 

Blocks can create a new scope and local scope in the block can reach outer scope
if we wanted to reach outer scope we need to make it a global or a constant or 
define a parameter and pass it as an argument.

In ruby every object pass by value and in ruby everything is object. Objects can be
two types: mutable and immutable. Immutables are Numbers and Boolean objects.
And every other objects are mutable. So what if we need to create a multiple mutable objects
in current context we should call New and pass it a block or proc.






[app_academy]: https://open.appacademy.io/learn/full-stack-online/full-stack-online-software-engineering-foundations/
[stackoverflow_question]: https://stackoverflow.com/questions/1788923/parameter-vs-argument 