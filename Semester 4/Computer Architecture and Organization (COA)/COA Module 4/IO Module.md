## Definition

An **I/O (Input/Output) module** is a hardware component that acts as an interface between the **processor and external devices**.  
It controls and manages the transfer of data between the **CPU, memory, and peripheral devices**.

---

# Functions of an I/O Module

The main functions of an I/O module are:

1. **Control and Timing**
2. **Processor Communication**
3. **Device Communication**
4. **Data Buffering**
5. **Error Detection**


---

# 1. Control and Timing

The I/O module controls the sequence and timing of data transfer.

- The processor communicates with one or more external devices at different times.
- Main memory and the system bus are shared by many activities including I/O operations.
- The I/O module coordinates and controls the transfer of data between internal resources and external devices.
    

---

# Data Transfer from Device to Processor

The steps involved are:

1. The processor checks the **status of the device** through the I/O module.
2. The I/O module sends the **device status** to the processor.
3. If the device is ready, the processor sends a **command to transfer data**.
4. The I/O module receives data (for example **8 or 16 bits**) from the external device.
5. The I/O module transfers the data to the **processor**.

If the system uses a **bus**, communication between the processor and the I/O module requires **bus arbitration**.

---

# 2. Processor Communication

The I/O module communicates with the processor in several ways.

## Command Decoding

- The I/O module receives commands from the processor through the **control bus**.
- Example commands for a disk drive:
    - READ SECTOR
    - WRITE SECTOR
    - SEEK track number
    - SCAN record ID
    
- Some commands include parameters sent through the **data bus**.
    

---

## Data Transfer

- Data is exchanged between the **processor and the I/O module** through the **data bus**.
    

---

## Status Reporting

- Peripheral devices are slow, so the processor must know the **status of the I/O module**.
- If the I/O module is busy with a previous command, it may not be ready.

Common status signals include:
- **BUSY**
- **READY**
    

Error conditions may also be reported to the processor.

---

## Address Recognition

- Each I/O device has a **unique address**.
- The I/O module must recognize the address of each peripheral it controls.
    

---

# 3. Device Communication

The I/O module also communicates directly with the **external device**.

This communication includes:
- Commands
- Status information
- Data transfer

---

# 4. Data Buffering

Data buffering is an important function of the I/O module.

- The data transfer rate of **main memory or processor is very high**, while many peripheral devices operate at **lower speeds**.
- Data from main memory is sent to the I/O module in a **rapid burst**.
- The I/O module **stores (buffers) the data temporarily**.

Then:
- The buffered data is sent to the peripheral device at its **own speed**.

In the reverse direction:
- Data from the device is buffered so that **memory is not delayed by slow transfers**.

Therefore, the I/O module operates at **both device speed and memory speed**.

If the I/O device works faster than memory, the I/O module performs buffering to **handle the speed difference**.

---

# 5. Error Detection

The I/O module detects errors and reports them to the processor.

Types of errors include:
- Mechanical or electrical problems (for example **paper jam or bad disk track**)
- Errors during transmission when **bit patterns change**
    

To detect these errors, **error detecting codes** are used.

---

## Parity Bit Method

A simple error detection method is the **parity bit**.

- In **IRA code**, 7 bits are used for the character.
- The **8th bit is used as a parity bit**.

The parity bit is set so that the total number of **1s** is:
- **Even parity** – even number of 1s
- **Odd parity** – odd number of 1s

When data is received, the I/O module checks the **parity bit** to detect errors.