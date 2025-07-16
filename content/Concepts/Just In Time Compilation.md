
# Without JIT

```python
# hello.py
print("Hello, Harsh!")
```

- **Source Code**: You write the `.py` file in plain Python.
- **Lexing**: Python breaks your code into tokens (e.g., `print`, `(`, `"Hello"`).
- **Parsing**: Python builds an **Abstract Syntax Tree (AST)** from tokens.
- **Compilation to Bytecode**:
    - Python compiles AST into **bytecode instructions** (intermediate code).
    - Stored in `.pyc` files inside `__pycache__/`.
- **Interpretation** by PVM:
    - The **Python Virtual Machine (PVM)** reads bytecode instructions **line by line** and performs the operations.
- **Execution**: The CPU runs the operations indirectly through the PVM.

At no point does CPython turn your code into **native machine code**.
The bytecode is **interpreted**, not compiled into fast, optimized machine code.
# With JIT

```python
from numba import jit

@jit
def add(a, b):
    return a + b

add(1, 2)  # Compiled to machine code on first call

```

- **Source Code**: Same `.py` file.
- **Tokenizing and Parsing**: Same as before → AST.
- **Bytecode Compilation**: Same — compiled to Python bytecode.
- **Start Execution**: Interpreter begins running bytecode.
- **JIT Monitoring**:
    - The JIT engine **monitors execution** to find “**hot**” functions (called very often).
    - Example: function inside a loop, used in numeric code.
- **Native Code Generation**:
    - JIT compiles the “hot” function into **machine code** at runtime.
    - That machine code is **stored in memory** and reused.
- **Fast Execution**:
    - Repeated calls to `add()` now **bypass bytecode** and go directly to **compiled machine code**.
    - ✅ Much faster.

so basically PVM goes back from interpreter to native code back and forth during runtime 

| Code Type             | #CPython Speed | #PyPy Speed (with JIT) |
| --------------------- | -------------- | ---------------------- |
| Simple scripts        | Similar        | Slightly better        |
| Heavy loops/functions | Slow           | 4–10x faster           |
| Numeric computation   | Very slow      | Close to C speed       |
