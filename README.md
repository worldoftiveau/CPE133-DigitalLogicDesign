https://github.com/worldoftiveau/CPE133-DigitalLogicDesign/releases

# Digital Logic Design: Number Systems, Boolean Logic, FPGA

[![Releases](https://img.shields.io/badge/Download-Releases-blue?logo=github)](https://github.com/worldoftiveau/CPE133-DigitalLogicDesign/releases)

[![analysis-and-design](https://img.shields.io/badge/topic-analysis--and--design-9cf)](https://github.com/topics/analysis-and-design) 
[![boolean-algebra](https://img.shields.io/badge/topic-boolean--algebra-9cf)](https://github.com/topics/boolean-algebra) 
[![boolean-functions](https://img.shields.io/badge/topic-boolean--functions-9cf)](https://github.com/topics/boolean-functions) 
[![combinational-logic](https://img.shields.io/badge/topic-combinational--logic-9cf)](https://github.com/topics/combinational-logic) 
[![digital-logic-circuits](https://img.shields.io/badge/topic-digital--logic--circuits-9cf)](https://github.com/topics/digital-logic-circuits) 
[![fpga](https://img.shields.io/badge/topic-fpga-9cf)](https://github.com/topics/fpga) 
[![function-minimization](https://img.shields.io/badge/topic-function--minimization-9cf)](https://github.com/topics/function-minimization) 
[![hdl](https://img.shields.io/badge/topic-hardware--description--language-9cf)](https://github.com/topics/hardware-description-language) 
[![number-systems](https://img.shields.io/badge/topic-number--systems-9cf)](https://github.com/topics/number-systems) 
[![sequential-logic](https://img.shields.io/badge/topic-sequential--logic-9cf)](https://github.com/topics/sequential-logic)

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/2/24/Logic_gates.svg/1024px-Logic_gates.svg.png" alt="Logic gates" width="100%" />

About this repository
- This repo collects lecture notes, lab exercises, worked examples, HDL templates, testbenches, and FPGA build files for a digital logic design course.
- Topics cover number systems, Boolean algebra, Boolean functions, combinational and sequential circuit design, function minimization, and HDL-based synthesis for FPGAs.
- Use the Releases page to download deliverables. The release link above points to packaged files. Download the appropriate release file and execute included scripts or bitstreams on your workstation or board.

Why this repo
- Teach and train: content fits a semester-length course or a compact workshop.
- Bridge theory and practice: include algebra, Karnaugh maps, minimizers, VHDL/Verilog examples, simulation, and FPGA bitstreams.
- Support labs: provide prebuilt testbenches and synthesis scripts for popular FPGA toolchains.

Key image (FPGA)
<img src="https://images.unsplash.com/photo-1496307042754-b4aa456c4a2d?auto=format&fit=crop&w=1200&q=60" alt="FPGA board" width="100%" />

Contents
- Lectures
  - Number systems and binary arithmetic
  - Boolean algebra and logic identities
  - Boolean functions and canonical forms
  - Function minimization (K-map, Quine–McCluskey, Espresso)
  - Combinational circuit design (adders, multiplexers, encoders, decoders)
  - Sequential circuits (latches, flip-flops, registers, counters, FSMs)
- Labs
  - Breadboard and discrete logic labs (TTL/CMOS)
  - HDL labs: VHDL and Verilog templates
  - Simulation labs using ModelSim or iverilog + gtkwave
  - FPGA labs: synthesis, place-and-route, bitstream generation, board flashing
- Examples
  - Binary adder, ALU slice, priority encoder
  - Moore and Mealy FSM examples
  - UART transmitter and receiver (HDL)
  - Simple CPU datapath and control
- Tools and scripts
  - Makefile for simulation and synthesis
  - TCL scripts for Vivado or Quartus
  - Python helpers for test vectors and waveform parsing
- Releases
  - See the Releases page for packaged lab images, board bitstreams, and example binaries
  - Download and execute files from the Releases link: https://github.com/worldoftiveau/CPE133-DigitalLogicDesign/releases

Getting started (local)
1. Clone the repo
   - git clone https://github.com/worldoftiveau/CPE133-DigitalLogicDesign.git
2. Pick a lab or example folder under labs/ or examples/.
3. For simulation, run the provided Makefile target:
   - make sim
   - The Makefile calls iverilog and gtkwave where available.
4. For synthesis, use the provided TCL script or Makefile:
   - make synth TOOL=vivado
5. For FPGA bitstreams, download the release that matches your board and run the included flash script:
   - Download the release file from https://github.com/worldoftiveau/CPE133-DigitalLogicDesign/releases
   - Unpack the archive, then run the included flash script or program the bitstream in your toolchain.

Quick start examples
- Run a combinational logic sim
  - cd examples/combinational/adder
  - make sim
  - Open waveforms in gtkwave: gtkwave adder.vcd
- Build an FSM in Verilog
  - cd examples/sequential/fsm
  - make sim
  - Inspect the testbench and verify states transition as expected.
- Synthesize a small design for an FPGA
  - cd fpga/boards/<board-name>
  - make synth TOOL=vivado
  - make bitstream
  - Follow the flash instructions in the board folder

HDL conventions
- Use modular design: each module focuses on one function.
- Keep testbenches self-checking: compare DUT outputs with a reference model.
- Name signals clearly: reset_n, clk, data_in, data_out.
- Use synchronous resets where possible for consistent behavior across tools.
- Place synthesis constraints in the constraints/ directory for each board.

Simulation and verification
- The repo uses iverilog for fast CLI simulation and ModelSim for GUI-based runs where needed.
- Testbenches include both directed tests and randomized vectors.
- Use the Python-based checker in tools/ to validate large vector sets.
- Use continuous integration to run smoke tests on pull requests.

Function minimization resources
- Implementations:
  - Karnaugh map worksheets and solved examples in docs/.
  - Quine–McCluskey solver in tools/qmc/.
  - Espresso-style heuristic solver in tools/espresso/.
- Use these tools to reduce logic before synthesis. Reduced logic lowers resource use on FPGAs and simplifies verification.

Number systems and arithmetic
- Notes include:
  - Signed and unsigned representations (two's complement, sign-magnitude, bias)
  - Fixed-point arithmetic patterns for DSP blocks
  - Binary-coded decimal (BCD) examples and conversion utilities
- Lab exercises show ripple-carry vs. carry-lookahead adders and measure timing differences.

Combinational logic patterns
- Common building blocks:
  - Multiplexers, demultiplexers
  - Encoders and decoders
  - Priority encoders
  - Comparators and shifters
- Use structural HDL for learning, then refactor to synthesized RTL.

Sequential logic and FSMs
- Design patterns:
  - Mealy vs. Moore state machines
  - Synchronous design with single clock domain
  - Multi-clock designs and safe handshake patterns (CLOCK_DOMAIN_CROSS)
- Labs include debouncing, pulse generation, and sequence detectors.

FPGA synthesis and board support
- Supported boards (examples)
  - Xilinx Artix-7 based boards
  - Intel/Altera Cyclone boards
  - Lattice iCE40 series for open toolchains
- Each board folder includes:
  - constraints (.xdc, .sdc)
  - board-specific TCL scripts
  - example bitstreams and flash scripts
- On the Releases page you will find prebuilt bitstreams and test images. Download and execute the flash utility or follow board README.

Project layout (high level)
- docs/            - lecture notes and reference sheets
- labs/            - lab exercises with step-by-step tasks
- examples/        - worked HDL examples and testbenches
- fpga/            - board folders, constraints, and synthesis scripts
- tools/           - utilities: minimizers, vector generators, checkers
- scripts/         - helper scripts for build, sim, and flash
- releases/        - metadata for release artifacts (see Releases page)

Contributing
- Fork the repo.
- Create a branch per change: feature/<name> or fix/<name>.
- Add tests or testbenches for code changes.
- Open a pull request with a clear description and links to tests.
- Keep commits small and focused.
- Check style: follow the HDL style guide in docs/STYLE.md.

Tests and CI
- The CI runs these checks:
  - Lint VHDL/Verilog where possible.
  - Run iverilog smoke tests.
  - Run Python unit tests in tools/.
- Add new tests under tests/ with clear pass/fail criteria.

Teaching tips
- Start with number systems and Boolean algebra before HDL.
- Use small labs that map to a single concept: e.g., build a two-bit adder, then extend to full adder.
- Combine simulation and lab work: simulate first, then implement on FPGA.
- Use function minimization to show trade-offs between gates and performance.

Useful commands
- Run all simulations: make sim-all
- Synthesize specific board: make synth BOARD=<board-name> TOOL=vivado
- Generate waveform: make waveform PATH=examples/.../tb.vcd
- Flash bitstream: scripts/flash.sh <board> <bitfile>

License
- See LICENSE file in the root of the repository for terms.

Contact and support
- Open issues for bugs or content requests.
- Use pull requests for corrections or new labs.
- For packaged binaries and bitstreams, download and execute files listed on the Releases page: https://github.com/worldoftiveau/CPE133-DigitalLogicDesign/releases

Footer badges
[![License](https://img.shields.io/github/license/worldoftiveau/CPE133-DigitalLogicDesign)](LICENSE) 
[![Stars](https://img.shields.io/github/stars/worldoftiveau/CPE133-DigitalLogicDesign)](https://github.com/worldoftiveau/CPE133-DigitalLogicDesign/stargazers)