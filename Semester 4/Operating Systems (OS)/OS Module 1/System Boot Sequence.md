## **Definition**

The **boot sequence** is the process of starting a computer and loading the **operating system into memory**.

---

## **Steps**

1. **Power On**
    - CPU starts executing firmware (**BIOS/UEFI**)
2. **POST (Power-On Self Test)**
    - Checks hardware (RAM, CPU, devices)
3. **Bootloader Loading**
    - BIOS/UEFI loads bootloader (e.g., GRUB) from disk
4. **Kernel Loading**
    - Bootloader loads OS kernel into memory
5. **Kernel Initialization**
    - Kernel initializes hardware and system resources
6. **Init Process Start**
    - First user-space process starts (e.g., `init` / `systemd`)
7. **System Ready**
    - Services start → login screen appears