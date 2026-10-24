# Assembly Lab — x86-64 Step-Through Visualizer

Learn x86-64 assembly by watching the hardware execute your code, cycle by cycle.

**Live demo:** https://arslancs1993.github.io/assembly/

## Features

- **64-bit register visualization** — all 16 GPRs (RAX–R15) shown as 64-bit values
- **Bit bars** — each register shows `[63......32......0]` with:
  - **Green bits** = value occupies this bit (RAX always green)
  - **Cyan bits** = active/changed this cycle
  - **Amber bit-32** = 32-bit width marker (shows where EAX ends)
- **Cycle-accurate micro-ops** — fetch → decode → execute, one clock per step
- **Datapath diagram** — register file, ALU, flags, memory, RIP with live wire highlighting
- **Memory view** — 256 bytes, hex + bit tooltip on hover
- **Flags** — ZF, CF, SF, OF with live updates
- **Assembly subset** — MOV, ADD/SUB/AND/OR/XOR, INC/DEC, SHL/SHR/SAR, CMP, JMP/Jcc, CALL/RET, PUSH/POP, NOP/HLT
- **NASM-style syntax** with labels
- **Keyboard control** → Step, Shift→ Step instruction, Space Run/Pause

## Quick Start

```bash
# Just open index.html in a browser — no build step, no dependencies
# Or serve locally:
python3 -m http.server 8080
# Then open http://localhost:8080
```

## Examples

Select from dropdown:
- **Hello RAX** — load immediate, copy, add
- **Loop counter** — DEC/JNZ loop
- **Bit shifts** — SHL/SHR demo
- **Memory ops** — store/load from memory
- **Stack demo** — PUSH/POP with RSP
- **Function call** — CALL/RET with argument in RDI

## Register Map

| 64-bit | 32-bit | 16-bit | 8-bit low | 8-bit high |
|--------|--------|--------|-----------|------------|
| RAX | EAX | AX | AL | AH |
| RBX | EBX | BX | BL | BH |
| RCX | ECX | CX | CL | CH |
| RDX | EDX | DX | DL | DH |
| RSI | ESI | SI | SIL | — |
| RDI | EDI | DI | DIL | — |
| RBP | EBP | BP | BPL | — |
| RSP | ESP | SP | SPL | — |
| R8–R15 | R8D–R15D | R8W–R15W | R8B–R15B | — |

## Bit Bar Legend

- <span style="color:#5ce27a;font-weight:bold">■</span> Green = bit holds value (RAX always)
- <span style="color:#2ee6d6;font-weight:bold">■</span> Cyan = changed this cycle
- <span style="color:#ffb020;font-weight:bold">■</span> Amber = bit 32 (32-bit boundary)
- <span style="color:#3a4a62">■</span> Dark = zero

## Architecture

Single-file HTML5 + vanilla JS (ES6). No frameworks, no build tools, no CDN — works from `file://` or GitHub Pages.

Inspired by `/root/cpu-lab/step-through-cpu.html` but extended for x86-64 with the bit-bar visualization requested.

## License

MIT