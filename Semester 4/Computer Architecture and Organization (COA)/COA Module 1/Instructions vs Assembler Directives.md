## 🔥 Definition

- **Instructions:**  
    Commands given to CPU to perform operations (like ADD, SUB)
- **Assembler Directives:**  
    Commands given to assembler to **organize program/data**, not executed by CPU

# ✍️ Difference between Instructions and Assembler Directives

| Aspect            | Instructions                                                 | Assembler Directives                                                             |
| ----------------- | ------------------------------------------------------------ | -------------------------------------------------------------------------------- |
| Definition        | Commands given to the CPU to perform specific operations     | Commands given to the assembler to organize the program or data                  |
| Executed by       | CPU executes instructions                                    | Not executed by CPU; interpreted by assembler                                    |
| Purpose           | Perform arithmetic, logic, data movement, control operations | Reserve memory, define data, control program assembly process                    |
| Examples          | ADD x1, x2, x3  <br>LW x1, num1  <br>SW x3, result           | .data, .text, .word, .ascii                                                      |
| Effect on Program | Directly affects the behavior of the program at runtime      | Helps assembler prepare programs for execution; does not affect runtime directly |