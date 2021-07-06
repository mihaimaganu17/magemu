# Stack
LIFO structure: Last in, first in
Instructions:
-> Push: Insert a new element at the top of the stack
-> Pop: Return the last element(top element) on the stack
-> Peek: Read the top element of the stack

On the X86 arch, the stack grows downwards.
The (CDECL)[https://en.wikibooks.org/wiki/X86_Disassembly/Calling_Conventions]
calling convention is the most widely used.

2 resgisters are used:
- ESP: Extended Stack Pointer. 32-bit value containing the top-of-stack address
- EBP: Extended Base Pointer. 32-bit value defining the current stack frame.
It points at the current local data. It can also access the routine parameters

# Conventions
The CDECL calling convention:
A. Caller's responsibilities
- Push parameters in reverse order(last parameter pushed first) Right-to-Left
- Perform the call
- Pop the parameters, use them, or simply increment ESP to remove them(stack
  clearing)
- The return value is stored in EAX

B. Callee's responsibilities(the routing being called)
- Store caller's EBP on the stack
- Save current ESP in EBP (mov EBP, ESP)
- Code, storing local data on the stack
- For a fast exit load the old ESP from EBP, else pop local data elements
- Pop the old EBP and return - store return value in EAX

The STDCALL calling convetion:


# Resources
http://eternal.red/2018/unicorn-engine-tutorial/
https://en.wikibooks.org/wiki/X86_Disassembly/Calling_Conventions
https://wiki.osdev.org/Stack
https://en.wikipedia.org/wiki/X86_calling_conventions
