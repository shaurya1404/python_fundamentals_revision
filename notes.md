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