# Basics

### Compile vs Interpreted

In a compiled language (like C, C++, or Rust), the entire source code is translated into machine code **before** the program ever runs.

**The Process:** You run your code through a program called a Compiler. It scans the entire project, checks for errors, and produces a separate executable file (like an .exe on Windows).

**The Analogy:** Imagine you have a Japanese cookbook. You send the entire book to a professional translator. A week later, they give you a copy written entirely in English. Now, you can cook whenever you want without needing the translator again.

In a purely interpreted language (like older versions of BASIC or some shell scripts), the code is translated line-by-line, on-the-fly.

**The Process:** A program called an Interpreter reads the first line of your code, converts it to machine code, executes it, and then moves to the second line.

**The Analogy:** You have that same Japanese cookbook, but this time you have a friend standing in the kitchen with you. They read the first instruction in Japanese, tell it to you in English, you do it, and then they read the next one.

**Common Misconception:** Python is "just" an interpreted language. In reality, it goes through a two-step process of comilation interpretation.

### Source Code

The script with the .py extention is human-readable but compete gibberish to the computer's CPU.

### Step One: Compilation Stage (Bytecode)

When you run your script, the Python interpreter first performs a hidden "compilation" step.

**The Process:** The interpreter checks your syntax. If it’s valid, it translates your high-level code into Bytecode.

**What is Bytecode?** It is a lower-level, platform-independent intermediate representation of your code. It isn't machine code (binary) yet, but it’s much closer to it than your original script.

**Storage:** Python often stores this bytecode in a folder called **__pycache__** as **.pyc** (compiled python) files. This saves time; if you don't change your code, Python skips the compilation step next time and loads the .pyc file directly.

### Step Two: The Python Virtual Machine

Once the bytecode is ready, it is sent to the PVM. Think of the PVM as the "engine" of Python.

**The Role of the PVM:** The PVM is a big loop that iterates through your bytecode instructions one by one.

**Interpretation:** The PVM translates each bytecode instruction into Machine Code (0s and 1s) that your specific processor (Intel, AMD, ARM) can actually execute.

**Platform Independence:** This is why Python is "portable." You can write code on Windows, and as long as a Mac has a PVM installed, it can run the same bytecode.

## Mutable vs Immutable

In Python, every piece of data is an object. When you assign a variable, you are creating a pointer (a reference) to a location in memory where that object lives.

The difference between Mutable and Immutable comes down to what happens when you try to change that object.

### Immutable Objects

**Types: int, float, string, tuple, bool**

If an object is immutable, you cannot change its contents once it is created. If you try to "modify" it, Python actually creates a brand-new object in a different memory location and moves your variable name to point to it.

```
x = 10
print(id(x))  # Output: 1407325 (Memory Address A)

x = x + 1
print(id(x))  # Output: 1407357 (Memory Address B)
```

### Mutable Objects

**Types: list, set, dict**

A mutable object can be changed in-place. The memory address (the "ID") stays the same, but the contents at that address are updated.

```
my_list = [1, 2]
print(id(my_list))  # Output: 2154880 (Memory Address C)

my_list.append(3)
print(my_list)      # Output: [1, 2, 3]
print(id(my_list))  # Output: 2154880 (Memory Address C)
```

### Why Does It Matter?

```
#Immutable Int
a = 10
b = a  # Both point to the same integer object '10' in memory

print(id(a))  # Output: 1407325 (Address X)
print(id(b))  # Output: 1407325 (Address X)

# Now, we "modify" b
b = b + 1 

print(a)      # Output: 10 (Remains unchanged!)
print(b)      # Output: 11 (A brand new object)

print(id(a))  # Output: 1407325 (Still Address X)
print(id(b))  # Output: 1407357 (New Address Y)

# Mutable List
list_a = [1, 2, 3]
list_b = list_a  # Both now point to the same address!

list_b.append(99)

print(list_a) # Output: [1, 2, 3, 99] 
# list_a changed even though we only touched list_b!

#Mutable List 2
list_a = [1, 2, 3]
list_b = [1, 2, 3]

list_b.append(44)

print(list_a) # Output: [1, 2, 3]
print(list_a) # Output: [1, 2, 3, 44] 
# memory reference will be different unless explicitly pointing to the same one (previous example)

#Mutable List 3
list_a = [1, 2, 3]
list_b = a[:] #slicing creates a copy - diferent memory references

list_b.append(88)

print(list_a) # Output: [1, 2, 3]
print(list_a) # Output: [1, 2, 3, 88]

# == vs is
m = [4, 5, 6]
n = m

m == n # Output: True - compares values
m is n # Output: True - compares memory reference

n = [4, 5, 6]

m == n # Output: True
m is n # Output: False
```