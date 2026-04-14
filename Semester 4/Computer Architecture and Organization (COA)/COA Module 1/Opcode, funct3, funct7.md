## **R-Type Instructions**

|Instruction|Opcode (dec)|funct3 (dec)|funct7 (dec)|
|---|---|---|---|
|ADD|51|0|0|
|SUB|51|0|32|
|AND|51|7|0|
|OR|51|6|0|
|XOR|51|4|0|
|SLL|51|1|0|
|SRL|51|5|0|
|SRA|51|5|32|
|SLT|51|2|0|

---

## **I-Type Instructions**

|Instruction|Opcode (dec)|funct3 (dec)|
|---|---|---|
|ADDI|19|0|
|ANDI|19|7|
|ORI|19|6|
|XORI|19|4|
|LW|3|2|
|JALR|103|0|

---

## **S-Type Instructions**

|Instruction|Opcode (dec)|funct3 (dec)|
|---|---|---|
|SW|35|2|

---

## **B-Type Instructions**

|Instruction|Opcode (dec)|funct3 (dec)|
|---|---|---|
|BEQ|99|0|
|BNE|99|1|
|BLT|99|4|
|BGE|99|5|

---

## **J-Type Instructions**

|Instruction|Opcode (dec)|
|---|---|
|JAL|111|