<div align="center">

# Page Replacement Algorithms Analysis

![Project Status: Active](https://img.shields.io/badge/status-active-brightgreen)
![GitHub license](https://img.shields.io/github/license/Code-Crew-Nexus/page-replacement-algorithms-analysis?color=purple)
![GitHub repo size](https://img.shields.io/github/repo-size/Code-Crew-Nexus/page-replacement-algorithms-analysis?color=blue)
![GitHub language count](https://img.shields.io/github/languages/count/Code-Crew-Nexus/page-replacement-algorithms-analysis?color=yellow)
![GitHub top language](https://img.shields.io/github/languages/top/Code-Crew-Nexus/page-replacement-algorithms-analysis?color=orange)
![GitHub last commit](https://img.shields.io/github/last-commit/Code-Crew-Nexus/page-replacement-algorithms-analysis?color=red)

![GitHub forks](https://img.shields.io/github/forks/Code-Crew-Nexus/page-replacement-algorithms-analysis?style=social)
![GitHub stars](https://img.shields.io/github/stars/Code-Crew-Nexus/page-replacement-algorithms-analysis?style=social)
![GitHub watchers](https://img.shields.io/github/watchers/Code-Crew-Nexus/page-replacement-algorithms-analysis?style=social)

---

## Languages & Tools

![C](https://img.shields.io/badge/C-00599C?logo=c&logoColor=white)
![Makefile](https://img.shields.io/badge/Makefile-000000?logo=gnu&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-0078D6?logo=windows&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?logo=linux&logoColor=black)

</div>

---

## What It Does

- Loads a **reference string** of page requests from user input  
- Accepts the **number of frames** available in memory  
- Simulates four algorithms step‑by‑step:
  - **FIFO (First-In, First-Out)** → replaces the oldest page in memory  
  - **LRU (Least Recently Used)** → replaces the page unused for the longest time  
  - **Optimal** → replaces the page not needed for the longest time in the future  
  - **LFU (Least Frequently Used)** → replaces the page with the lowest usage frequency  
- Prints a **trace table** showing frames after each request and whether it was a HIT or FAULT  
- Summarizes **total page faults** for each algorithm  
- Compares results side‑by‑side to highlight differences in efficiency  
- Works seamlessly on **Windows 11 (MinGW/MSYS2)** and **Linux (Arch/Ubuntu)** using the provided Makefile  

---

## Overview

This project implements and compares **Page Replacement Algorithms** as part of an Operating Systems Problem-Based Learning (PBL) assignment. It demonstrates how different strategies handle memory management when pages are requested by a process but limited frames are available.

---

## Project Structure

```project-structure
page-replacement-algorithms-analysis/
│
├── docs/                        # Documentation folder (reports, diagrams, extended notes)
│
├── src/                         # Source code folder
│   ├── algorithms.h             # Header file declaring prototypes for all algorithms
│   ├── fifo.c                   # FIFO algorithm implementation
│   ├── fifo.o                   # Compiled object file for FIFO
│   ├── lfu.c                    # LFU algorithm implementation
│   ├── lfu.o                    # Compiled object file for LFU
│   ├── lru.c                    # LRU algorithm implementation
│   ├── lru.o                    # Compiled object file for LRU
│   ├── optimal.c                # Optimal algorithm implementation
│   ├── optimal.o                # Compiled object file for Optimal
│   ├── utils.c                  # Utility functions (printing, helpers, frequency tracking)
│   ├── utils.h                  # Header file for utility functions
│   ├── utils.o                  # Compiled object file for utils
│   ├── main.c                   # Entry point: handles input, calls algorithms, prints results
│   ├── main.o                   # Compiled object file for main
│   ├── Makefile                 # Cross-platform build script (Windows + Linux)
│   ├── page_replacement         # Linux executable (built via `make`)
│   └── page_replacement.exe     # Windows executable (built via `mingw32-make`)
│
└── README.md                    # Project documentation (overview, usage, algorithms, contributors)
```

---

### 🔹 Notes on Structure
- **`src/`** contains all source code and compiled artifacts.  
- **`.c` files** → algorithm implementations and utilities.  
- **`.h` files** → function prototypes and shared declarations.  
- **`.o` files** → intermediate object files generated during compilation.  
- **Executables** (`page_replacement`, `page_replacement.exe`) are generated depending on OS.  
- **`docs/`** can be used for reports, diagrams, or extended documentation.  
- **`README.md`** provides usage instructions, algorithm explanations, and contributor credits.  

---

Here’s a **Requirements section** you can add separately to your README.md. It clearly lists what’s needed to build and run the project on both Windows and Linux:

---

## Requirements

To build and run this project successfully, ensure the following prerequisites are installed and configured:

### 🔹 General
- A working **Git** installation (for cloning and version control).
- Basic knowledge of **C programming** and **Makefiles**.

### 🔹 On Linux (Arch/Ubuntu)
- **GCC (GNU Compiler Collection)**  
  Install via package manager:  
  ```bash
  sudo pacman -S gcc        # Arch Linux
  sudo apt-get install gcc  # Ubuntu/Debian
  ```
- **Make (GNU Make)**  
  ```bash
  sudo pacman -S make       # Arch Linux
  sudo apt-get install make # Ubuntu/Debian
  ```

### 🔹 On Windows 11
- **MSYS2/MinGW-w64 environment**  
  Download and install from [MSYS2](https://www.msys2.org/).  
- Update packages:  
  ```bash
  pacman -Syu
  ```
- Install required toolchain:  
  ```bash
  pacman -S mingw-w64-ucrt-x86_64-gcc mingw-w64-ucrt-x86_64-make
  ```
- Use **PowerShell** or **MSYS2 terminal** to run `mingw32-make`.

### 🔹 Optional Tools
- **VS Code** or any IDE/editor for editing source files.
- **GitHub Desktop** or CLI for managing commits and pushes.
- **Markdown previewer** for viewing README.md formatting.

---

## Repository Setup

### Clone the Repository
```bash
git clone https://github.com/Code-Crew-Nexus/page-replacement-algorithms-analysis.git
cd page-replacement-algorithms-analysis/src
```

---

## Compilation & Execution

This project uses a **cross-platform Makefile** that works on both **Windows 11 (MinGW/MSYS2)** and **Linux (Arch, Ubuntu, etc.)**.

### On Arch/Linux
```bash
make clean
make
make run
```

### On Windows 11 (PowerShell with MinGW/MSYS2)
```powershell
mingw32-make clean
mingw32-make
mingw32-make run
```

The Makefile automatically detects the OS and builds the correct executable (`page_replacement` on Linux, `page_replacement.exe` on Windows).

---

## Main Logic of the Code

The program simulates page replacement algorithms by:
1. Taking input:
   - Number of pages in the reference string
   - The reference string itself
   - Number of frames available
2. Iterating through each page request:
   - Checking if the page is already in memory (HIT).
   - If not, applying the chosen algorithm to decide which page to replace (FAULT).
3. Printing a step-by-step trace of frames and results.
4. Summarizing total page faults for each algorithm.

---

## Algorithms Explained

### 1. FIFO (First-In, First-Out)
- **Definition:** Replace the oldest page in memory (the one loaded earliest).
- **Formula:** Replace `page[i - frame_count]` when a fault occurs.
- **Example:**  
  Reference string: `1 2 3 4 1 2 5` with 3 frames → FIFO faults = 6.

### 2. LRU (Least Recently Used)
- **Definition:** Replace the page that has not been used for the longest time.
- **Formula:** Replace the page with the **minimum last-used timestamp**.
- **Example:**  
  Reference string: `1 2 3 4 1 2 5` with 3 frames → LRU faults = 5.

### 3. Optimal
- **Definition:** Replace the page that will not be used for the longest time in the future.
- **Formula:** Replace the page with the **maximum next-use distance**.
- **Example:**  
  Reference string: `1 2 3 4 1 2 5` with 3 frames → Optimal faults = 4.

### 4. LFU (Least Frequently Used)
- **Definition:** Replace the page with the lowest usage frequency.
- **Formula:** Replace the page with the **minimum frequency count**.
- **Example:**  
  Reference string: `1 2 3 4 1 2 5` with 3 frames → LFU faults = 5.

---

## Differences Between Algorithms

| Algorithm | Strategy | Strength | Weakness |
|-----------|----------|----------|----------|
| FIFO      | Oldest page replaced | Simple, easy to implement | May evict frequently used pages |
| LRU       | Least recently used | Good approximation of optimal | Requires tracking usage history |
| Optimal   | Furthest future use | Lowest possible faults | Not implementable in real systems (needs future knowledge) |
| LFU       | Least frequently used | Keeps popular pages | May evict recent but important pages |

---

## Sample Input/Output

**Input:**
```
Enter number of pages in reference string: 12
Enter the reference string (space-separated): 1 2 3 4 1 2 5 1 2 3 4 5
Enter number of frames: 3
```

**Output:**
```
---- FIFO Simulation ----
Page   Frames      Result
1      1  -  -     FAULT   
2      1  2  -     FAULT   
3      1  2  3     FAULT   
4      4  2  3     FAULT   
1      4  1  3     FAULT   
2      4  1  2     FAULT   
5      5  1  2     FAULT   
1      5  1  2     HIT     
2      5  1  2     HIT     
3      5  3  2     FAULT   
4      5  3  4     FAULT   
5      5  3  4     HIT     
Total Page Faults (FIFO): 9

----  LRU Simulation ----
Page   Frames      Result
1      1  -  -     FAULT   
2      1  2  -     FAULT   
3      1  2  3     FAULT   
4      4  2  3     FAULT   
1      4  1  3     FAULT   
2      4  1  2     FAULT   
5      5  1  2     FAULT   
1      5  1  2     HIT     
2      5  1  2     HIT     
3      3  1  2     FAULT   
4      3  4  2     FAULT   
5      3  4  5     FAULT   
Total Page Faults (LRU): 10

--- Optimal Simulation ---
Page   Frames      Result
1      1  -  -     FAULT   
2      1  2  -     FAULT   
3      1  2  3     FAULT   
4      1  2  4     FAULT   
1      1  2  4     HIT     
2      1  2  4     HIT     
5      1  2  5     FAULT   
1      1  2  5     HIT     
2      1  2  5     HIT     
3      3  2  5     FAULT   
4      4  2  5     FAULT   
5      4  2  5     HIT     
Total Page Faults (Optimal): 7

----  LFU Simulation ----
Page   Frames      Result
1      1  -  -     FAULT   
2      1  2  -     FAULT   
3      1  2  3     FAULT   
4      4  2  3     FAULT   
1      1  2  3     FAULT   
2      1  2  3     HIT     
5      5  2  3     FAULT   
1      1  2  3     FAULT   
2      1  2  3     HIT     
3      1  2  3     HIT     
4      4  2  3     FAULT   
5      5  2  3     FAULT   
Total Page Faults (LFU): 9
```

**Output (summary):**
```
=== Final Page Replacement Analysis ===
FIFO Page Faults   : 9
LRU Page Faults    : 10
Optimal Page Faults: 7
LFU Page Faults    : 9
```

---

## Conclusion

This project provides a comprehensive analysis of **Page Replacement Algorithms** — FIFO, LRU, Optimal, and LFU — by simulating their behavior on given reference strings and comparing their performance. It demonstrates how different strategies handle page faults when memory frames are limited, highlighting the trade‑offs between simplicity, efficiency, and practicality in operating system design.

- **FIFO** is straightforward but often inefficient, as it may evict frequently used pages.  
- **LRU** improves efficiency by tracking usage history, closely approximating optimal behavior.  
- **Optimal** achieves the lowest possible faults but is theoretical, requiring future knowledge.  
- **LFU** favors frequently used pages but can penalize recently important ones.  

The project is designed with a **cross‑platform Makefile**, ensuring seamless compilation and execution on both **Windows 11 (MinGW/MSYS2)** and **Linux (Arch/Ubuntu)**. With clear documentation, structured source code, and sample input/output demonstrations, this repository serves as both an academic resource and a practical tool for understanding memory management strategies in operating systems.

---

## Contributors
- M. Sai Krishna  
- Md. Abdul Rayain  
- Rishit Ghosh  
- Y. Karthik  
> Future contributors welcome! Fork the repo, submit pull requests, and help improve the project. 

---

## Notes
- Optimal is theoretical and always gives the lowest page faults.
- FIFO is simplest but often inefficient.
- LRU and LFU approximate real-world scenarios better.
- This project demonstrates the **trade-offs in memory management** strategies.

---