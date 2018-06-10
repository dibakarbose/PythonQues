
# Python Interview Questions

### Q1. What are the key features of Python?

These are the few key features of Python:
<ol>
<li> Python is an <strong>interpreted</strong> language. That means that, unlike languages like C and its variants, Python does not need to be compiled before it is run. Other interpreted languages include PHP and Ruby.</li>
<li>Python is <strong>dynamically</strong> typed, this means that you don’t need to state the types of variables when you declare them or anything like that. You can do things like x=111 and then x="I'm a string" without error</li>
<li>Python is well suited to <strong>object oriented programming</strong> in that it allows the definition of classes along with composition and inheritance. Python does not have access specifiers (like C++’s public, private), the justification for this point is given as “we are all adults here”</li>
<li>In Python, <strong><u>functions are first-class objects</u></strong>. This means that they can be assigned to variables, returned from other functions and passed into functions. Classes are also first class objects</li>
<li><strong>Writing Python code is quick</strong> but running it is often slower than compiled languages. Fortunately，Python allows the inclusion of C based extensions so bottlenecks can be optimized away and often are. The numpy package is a good example of this, it’s really quite quick because a lot of the number crunching it does isn’t actually done by Python</li>
<li>Python finds use in many spheres – <em>web applications, automation, scientific modelling, big data applications</em> and many more. It’s also often used as “glue” code to get other languages and components to play nice.</li>
</ol>

### Q2. What is the difference between deep and shallow copy?

<strong><em>Shallow copy</em></strong> is used when a new instance type gets created and it keeps the values that are copied in the new instance. Shallow copy is used to copy the reference pointers just like it copies the values. These references point to the original objects and the changes made in any member of the class will also affect the original copy of it. Shallow copy allows faster execution of the program and it depends on the size of the data that is used.

<strong><em>Deep copy</em></strong> is used to store the values that are already copied. Deep copy doesn’t copy the reference pointers to the objects. It makes the reference to an object and the new object that is pointed by some other object gets stored. The changes made in the original copy won’t affect any other copy that uses the object. Deep copy makes execution of the program slower due to making certain copies for each object that is been called.


```python
#References
l1=[1,2,3,4]
l2=l1
l2.append(11)
print(l1)
print(l2)
```

    [1, 2, 3, 4, 11]
    [1, 2, 3, 4, 11]
    


```python
#Shallow Copy
import copy
l3=copy.copy(l1)  #l3 will have same value as l1
l3.append(10)
print("l1 = ",l1)
print("l2 = ",l2)
print("l3 = ",l3)
```

    l1 =  [1, 2, 3, 4, 11]
    l2 =  [1, 2, 3, 4, 11]
    l3 =  [1, 2, 3, 4, 11, 10]
    


```python
#Deep Copy
l4=copy.deepcopy(l1)
l4.append(23)
print("l1 = ",l1)
print("l2 = ",l2)
print("l3 = ",l3)
print("l4 = ",l4)
```

    l1 =  [1, 2, 3, 4, 11]
    l2 =  [1, 2, 3, 4, 11]
    l3 =  [1, 2, 3, 4, 11, 10]
    l4 =  [1, 2, 3, 4, 11, 23]
    

### Q3. What is the difference between list and tuples?

<em>Lists</em> are mutable i.e they can be edited. 
Syntax: list_1 = [10, ‘Chelsea’, 20]

<em>Tuples</em> are immutable (tuples are lists which can’t be edited). 
Syntax: tup_1 = (10, ‘Chelsea’ , 20)

When you have fixed data and you know the size then you use tuple, Otherwise you can use list

Fixed Memory,Fixed data,Memory intensice task--> Always use tuples
Buffers, Queues, Stacks --> Always use lists

### Q4. How is Multithreading achieved in Python?

<ul>
<li>Python has a multi-threading package but if you want to multi-thread to speed your code up.</li>
<li>thon has a construct called the Global Interpreter Lock (GIL). The GIL makes sure that only one of your ‘threads’ can execute at any one time. A thread acquires the GIL, does a little work, then passes the GIL onto the next thread.</li>
<li>This happens very quickly so to the human eye it may seem like your threads are executing in parallel, but they are really just taking turns using the same CPU core.</li>
<li>All this GIL passing adds overhead to execution. This means that if you want to make your code run faster then using the threading package often isn’t a good idea.</li>
</ul>

Module to use :: <em>multiprocessing</em> and <em>threading</em>

### Q5. How can the ternary operators be used in python?

The Ternary operator is the operator that is used to show the conditional statements. This consists of the true or false values with a statement that has to be evaluated for it.

<strong>Syntax:</strong><br>
The Ternary operator will be given as:<br>
[on_true] if [expression] else [on_false]x, y = 25, 50

<blockquote>big = x if x < y else y</blockquote>
The expression gets evaluated as in this case if x less than y is true then the value is returned as big=x and if it is incorrect then big=y will be sent as a result.

### Q6. How is memory managed in Python?

<ol>
<li>Python memory is managed by Python private heap space. All Python objects and data structures are located in a private heap. The programmer does not have an access to this private heap and interpreter takes care of this Python private heap. </li>
<li>The allocation of Python heap space for Python objects is done by Python memory manager. The core API gives access to some tools for the programmer to code.</li>
<li>Python also have an inbuilt garbage collector, which recycles all the unused memory and frees the memory and makes it available to the heap space.</li>
</ol>

### Q7. What is monkey patching in Python?

In Python the term monkey patch only refers to the dynamic modifications of a class or module at run-time.

Consider the below example
<blockquote>
<code>
#m.py
class MyClass:
    def f(self):
        print("In f()")
</code>
</blockquote>

We can run the monkey-patch testing like this
<blockquote>
<code>
import m
def monkey_f(self):
print("In monkey_f()")
 
m.MyClass.f = monkey_f
obj = m.MyClass()
obj.f()
</code>
</blockquote>

The output will be as below:
<blockquote><code>In monkey_f()</code></blockquote>

As we can see, we did make some changes in the behavior of f() in <em>MyClass</em> using the function we defined, <em>monkey_f()</em>, outside of the module <em>m</em>.

### Q8. How can you randomize the items of a list in place in Python?

Consider the example shown below:
<blockquote>
<code>from random import shuffle
x = ['Keep', 'The', 'Blue', 'Flag', 'Flying', 'High']
shuffle(x)
print(x)
</code>
</blockquote>

The output of the following code is as below.<br>
<blockquote>
<code>['Keep', 'The', 'Blue', 'High', 'Flag', 'Flying']</code>
</blockquote>

### Q9. Write a sorting algorithm for a numerical dataset in Python.

The following code can be used to sort a list in Python:
<blockquote>
<code>l1 = ["1", "4", "0", "6", "9"]
l1 = [int(i) for i in l1]
l1.sort()
print(l1)</code>
</blockquote>

Another way to do the above operation:
<blockquote>
<code>l1 = ["1", "4", "0", "6", "9"]
l1 = map(int,l1)
l1=list(l1)    #Map object has to be converted to list object for further operation
l1.sort()
print(l1)</code>
</blockquote>
