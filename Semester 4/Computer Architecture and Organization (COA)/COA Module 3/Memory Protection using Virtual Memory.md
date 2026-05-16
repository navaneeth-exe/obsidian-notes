
## **Definition**

Memory protection is the mechanism that **prevents one program from accessing or modifying another program’s memory**.


In multiprogramming systems, multiple programs run simultaneously and share physical memory. Memory protection ensures that one program cannot access or modify another program’s memory.

Preventing unauthorized access to another program’s memory is called memory protection.

Virtual memory provides memory protection by giving each program its own virtual address space.

The virtual address space of a program is independent of other programs and gives the illusion of exclusive access to memory.

During execution, programs generate virtual addresses, which are translated into physical addresses using the page table.

If a virtual page is not mapped in the page table, the program cannot access that physical memory location.

Thus, virtual memory prevents unauthorized access and ensures safe execution of programs.