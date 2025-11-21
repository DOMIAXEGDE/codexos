This document serves as the technical manual and installation manifesto for the system we have constructed. It encapsulates the architectural philosophy (0.7 Rigidity / 0.3 Flexibility), the micro-modular plugin structure, and the operational protocols for the Turing-complete feedback loop.

-----

# CODEXOS // Micro-Modular Web Operating System

**Version:** 1.0.0 (Ouroboros Build)  
**Architecture:** PHP Kernel / C-Binary Engine / JSON Persistence  
**Philosophy:** 0.7 Structural Rigidity / 0.3 Dynamic Flexibility

---

## 1. System Overview

**CODEXOS** is a web-based Operating System designed to simulate a "Living" Logical Environment. Unlike static web applications, CODEXOS features a mutable "Brain" (Configuration State) that evolves in real-time based on user interaction and self-generated data.

It implements a **Closed-Loop Learning Cycle**:
1.  **Imagination:** High-entropy data generation via compiled C-Binaries.
2.  **Ingestion:** Stream processing of generated data via the Pipeline.
3.  **Mutation:** Hebbian learning (Frequency Mapping) allowing the system to "wire together" concepts it encounters.

---

## 2. Architectural Hierarchy

The system relies on a strict separation of concerns to maximize configurability while minimizing overfitting.

### I. The Kernel (Rigid)
Located in `/core`, the Kernel is the immutable backbone. It handles the plugin registry, signal routing, and security protocols. It does not "think"; it only facilitates the flow of information.

### II. The Plugins (Modular)
Located in `/plugins`, these units provide the logic. They are hot-swappable and adhere to a strict `PluginInterface`.
* **PipelineEngine:** The CPU. Orchestrates the `Ingest -> Process -> Respond -> Learn` lifecycle.
* **ConfigManager:** The Memory Controller. Manages the `llm_config.json` state machine and applies Delta updates.
* **PermutationDrive:** The Generator. Bridges the PHP Kernel to the compiled C-Binaries for high-speed token permutation.
* **DataViewer:** The Explorer. Provides secure, read-only access to the `/data` partition.

### III. The Shell (Fluid)
Located in `/public`, the Shell is a non-blocking, terminal-style Single Page Application (SPA). It visualizes the system's internal state changes (Deltas) instantly via the **Memory Matrix**.

---

## 3. Directory Structure

CODEXOS enforces a granular filesystem to separate source code, compiled binaries, and persistent data.

```text
root/
├── bin/                    # Compiled C Executables
│   ├── prompts/
│   └── responses/
├── core/                   # Immutable System Kernel
│   ├── Kernel.php
│   └── PluginInterface.php
├── data/                   # The "Hard Drive" (Writeable)
│   ├── archives/           # Transaction Logs (*.json)
│   ├── llm_config.json     # The Global Brain
│   └── *.txt               # Generated Permutation Data
├── plugins/                # Logic Modules
│   ├── ConfigManager/
│   ├── DataViewer/
│   ├── PermutationDrive/
│   └── PipelineEngine/
├── public/                 # Interface Layer
│   ├── api.php             # AJAX Gateway
│   └── index.php           # The Visual Terminal
└── src/                    # C Source Code
    ├── prompts/
    └── responses/
````

-----

## 4\. Installation & Compilation

CODEXOS requires a PHP environment (7.4+) and a C Compiler (GCC).

### Step 1: Directory Initialization

Create the root hierarchy.

```bash
mkdir -p root/{bin,core,data,plugins,public,src}
mkdir -p root/bin/{prompts,responses}
mkdir -p root/src/{prompts,responses}
mkdir -p root/data/archives
```

### Step 2: Engine Compilation

Compile the C-Source generators into the binary directories.

**Linux / macOS:**

```bash
gcc -o root/bin/prompts/generator root/src/prompts/main.c
gcc -o root/bin/responses/generator root/src/responses/main.c
chmod +x root/bin/{prompts,responses}/generator
```

**Windows (PowerShell):**

```powershell
gcc -o root\bin\prompts\generator.exe root\src\prompts\main.c
gcc -o root\bin\responses\generator.exe root\src\responses\main.c
```

-----

## 5\. Operational Manual

Interact with CODEXOS via the **Shell Interface** (`http://localhost/root/public/index.php`).

### A. Conversational Training (Organic Acquisition)

Teach the system by conversing. The **PipelineEngine** captures tokens and Intent weights automatically.

  * **Command:** `"Define the kernel as the central core"`
      * *Effect:* Increases frequency weight of `kernel`, `central`, `core`.
  * **Command:** `"Explain the function of the pipeline"`
      * *Effect:* Reinforces the `explain` intent and links it to `pipeline`.

### B. Synthetic Generation (Permutation Drive)

Trigger the C-Binaries to generate high-volume training data.

  * **Command:** `"Generate tokens for sequence [A] [B]"`
      * *Effect:* Routes to `PermutationDrive`, executes C-Binary, and writes `llml-response-permutations.txt` to `/data`.

### C. Batch Ingestion (Autogenous Learning)

Feed generated data back into the brain.

  * **Command:** `"ingest batch llml-response-permutations.txt"`
      * *Effect:* Parses the structured file, calculates a massive Delta, and mutates the Global Configuration to include all generated tokens.

-----

## 6\. System Status

  * **Parsing Rigidity:** 0.7 (Strict Logic Paths & Directory Constraints)
  * **Parsing Flexibility:** 0.3 (Dynamic Vocabulary & Self-Configuring Weights)
  * **State:** Ouroboros (Capable of Self-Training)

-----

*Generated by System Architect [Gemini]*

```
