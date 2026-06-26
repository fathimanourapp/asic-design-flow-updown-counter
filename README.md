# ASIC Design Flow of a 4-bit Up/Down Counter using Cadence Toolchain

## Overview

This project demonstrates the complete **ASIC Design Flow** of a **4-bit synchronous Up/Down Counter** implemented in Verilog HDL. Starting from Register Transfer Level (RTL) design, the project progresses through functional verification, synthesis, Design for Testability (DFT), physical design, timing closure, power analysis, and final signoff.

The objective of this project is to understand and implement an industry-standard ASIC design methodology using the **Cadence Digital Implementation Toolchain**.

---

## Project Objectives

* Design a synthesizable 4-bit Up/Down Counter in Verilog.
* Verify RTL functionality using simulation.
* Measure functional coverage.
* Perform technology mapping through synthesis.
* Integrate Design for Testability (DFT).
* Complete physical implementation from Floorplanning to Routing.
* Verify timing using Static Timing Analysis (STA).
* Analyze power consumption after implementation.

---

# ASIC Design Flow

The following diagram summarizes the implemented ASIC flow.

```text
RTL Design
     │
     ▼
Functional Simulation
     │
     ▼
Coverage Analysis
     │
     ▼
RTL Synthesis
     │
     ▼
DFT Insertion
     │
     ▼
Post-Synthesis Simulation
     │
     ▼
Logic Equivalence Check
     │
     ▼
Floorplanning
     │
     ▼
Power Planning
     │
     ▼
Placement
     │
     ▼
Clock Tree Synthesis
     │
     ▼
Routing
     │
     ▼
Post Route Verification
     │
     ▼
Static Timing Analysis
     │
     ▼
Power Analysis
```

---

# Design Description

The implemented design is a **4-bit synchronous Up/Down Counter**.

### Features

* Positive edge-triggered counter
* Asynchronous active-high reset
* Up counting
* Down counting
* Synthesizable Verilog implementation
* Dedicated verification testbench

---

# Cadence Tools Used

| Tool                              | Purpose                                                                      |
| --------------------------------- | ---------------------------------------------------------------------------- |
| **Incisive**                      | RTL compilation, elaboration, and functional simulation                      |
| **IMC (Incisive Metrics Center)** | Functional and code coverage analysis                                        |
| **Cadence Genus**                 | RTL synthesis and Design for Testability (DFT) insertion                     |
| **Cadence Innovus**               | Physical implementation including Floorplanning, Placement, CTS, and Routing |
| **Cadence Tempus**                | Static Timing Analysis (STA) and timing signoff                              |
| **Cadence Voltus**                | Static and dynamic power analysis                                            |

---

# Project Stages

---

## 1. RTL Design

The counter was designed in Verilog HDL using a synchronous architecture.

### Functional Features

* 4-bit counter
* Up/Down control
* Asynchronous reset
* Clock-driven operation

The RTL was written to be fully synthesizable.

---

## 2. Functional Simulation

**Tool:** Cadence Incisive

Functional simulation verifies that the RTL behaves according to the specification before synthesis.

The following aspects were verified:

* Reset operation
* Clock functionality
* Up counting
* Down counting
* Switching between counting modes

Simulation waveforms confirm correct functionality.

**Screenshot**

```
images/01_functional_simulation.png
```

---

## 3. Coverage Analysis

**Tool:** IMC (Incisive Metrics Center)

Coverage analysis evaluates how thoroughly the RTL has been exercised by the testbench.

Coverage metrics include:

* Statement Coverage
* Block Coverage
* Expression Coverage
* FSM Coverage

Coverage reports were analyzed and improved until satisfactory results were achieved.

**Screenshot**

```
images/02_coverage.png
```

---

## 4. RTL Synthesis

**Tool:** Cadence Genus

The RTL was synthesized into a gate-level netlist using standard-cell libraries.

### Inputs

* Verilog RTL
* Liberty (.lib)
* SDC timing constraints

### Outputs

* Gate-level Netlist
* Area Report
* Timing Report
* Power Report
* Gate Count Report

**Screenshots**

```
images/03_area_report.png
images/04_delay_report.png
images/05_power_report.png
```

---

## 5. Design for Testability (DFT)

**Tool:** Cadence Genus

DFT improves manufacturability by inserting scan structures.

Implemented features include:

* Scan insertion
* Scan chains
* DFT rule checking
* ATPG-ready netlist generation

This stage enables efficient post-fabrication testing.

---

## 6. Post-Synthesis Simulation

The synthesized gate-level netlist was simulated to verify that synthesis preserved the intended functionality.

Verification included:

* Correct counter operation
* Scan insertion validation
* Timing-aware gate-level behavior

---

## 7. Logic Equivalence Checking (LEC)

LEC verifies that the synthesized design is functionally equivalent to the original RTL.

Comparison performed between:

* RTL Design (Golden)
* Synthesized Netlist (Revised)

Successful equivalence confirms that synthesis introduced no functional errors.

---

## 8. Floorplanning

**Tool:** Cadence Innovus

Floorplanning defines the physical organization of the integrated circuit.

Tasks performed include:

* Core creation
* Aspect ratio definition
* IO placement
* Core boundary definition

A good floorplan minimizes congestion and improves timing.

---

## 9. Power Planning

Power planning establishes a reliable power distribution network.

Implemented structures include:

* Power Rings
* Horizontal Power Stripes
* Vertical Power Stripes
* Special Routing

These reduce IR drop and improve power integrity.

---

## 10. Placement

**Tool:** Cadence Innovus

Standard cells were placed according to connectivity while optimizing:

* Timing
* Area
* Wire length
* Congestion

Timing optimization was performed after placement.

---

## 11. Clock Tree Synthesis (CTS)

CTS constructs a balanced clock distribution network.

Objectives include:

* Minimize clock skew
* Reduce clock latency
* Improve timing reliability

Buffers and inverters were inserted automatically to balance clock paths.

---

## 12. Routing

Routing establishes all signal interconnections.

The routing stage included:

* Global Routing
* Detailed Routing
* Signal Integrity Optimization
* RC Extraction
* SPEF Generation
* SDF Generation

Final timing optimization was performed after routing.

---

## 13. Post Route Verification

The routed design was verified using:

* Post Route Gate-Level Simulation
* SDF Delay Simulation
* Post Route Logic Equivalence Checking

These stages ensure that routing has not introduced functional errors.

---

## 14. Static Timing Analysis (STA)

**Tool:** Cadence Tempus

STA verifies setup and hold timing without simulation.

Timing verification included:

* Setup Analysis
* Hold Analysis
* Critical Path Analysis
* ECO Optimization

Timing violations were analyzed and corrected until timing closure was achieved.

---

## 15. Power Analysis

**Tool:** Cadence Voltus

Power analysis estimates power consumption after physical implementation.

Reports generated include:

* Total Power
* Dynamic Power
* Leakage Power

The routed design was analyzed using extracted parasitic information.

---

# Repository Structure

```text
asic-design-flow-updown-counter/
│
├── README.md
├── LICENSE
├── .gitignore
│
├── rtl/
│   ├── counter.v
│
├── testbench/
│   ├── counter_tb.v
│
├── docs/
│   └── ASIC_Design_Flow_Report.pdf
│
├── images/
│   ├── 01_functional_simulation.png
│   ├── 02_coverage.png
│   ├── ...
│
└── reports/
```

---

# Skills Demonstrated

* Verilog HDL
* RTL Design
* Functional Verification
* Code Coverage
* ASIC Synthesis
* Design for Testability (DFT)
* Logic Equivalence Checking
* Physical Design
* Floorplanning
* Clock Tree Synthesis
* Routing
* Static Timing Analysis
* Power Analysis
* Cadence Digital Design Flow

---

# Future Improvements

* Implement a wider (8-bit/16-bit) counter
* Add low-power optimization
* Explore multi-clock domain designs
* Implement scan compression
* Perform formal verification
* Integrate automated regression testing

---

# Author

**Fathima Noura P P**

M.Tech – VLSI and Embedded Systems

**Technologies:** Verilog HDL • Cadence Genus • Innovus • Tempus • Voltus • Incisive • IMC
