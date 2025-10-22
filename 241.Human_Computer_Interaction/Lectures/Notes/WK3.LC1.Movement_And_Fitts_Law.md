---
date: 2025-10-21
noted: false
tags:
  - week3
  - doitlater
---
```table-of-contents
```

> [!info] Resources
> [📊 PowerPoint]()
> [📽️Lecture Recording]()

---
## Human Movement & Fitts’ Law 

### 📘 Learning Objectives
---
## Fitts’ Law Overview
Proposed by **Paul Fitts (1954)**, a psychologist and human factors pioneer, to describe **how long it takes to move to a known target**.

Movement time (MT) depends on:
- **Distance (D)** → target distance.
- **Width (W)** → target size/tolerance.

**Closer or larger targets = faster movement.**  
**Farther or smaller targets = slower, more accurate movement.**

---
## Fitts’ Experiment
- 4 distances (2, 4, 8, 16 in) × 4 widths (0.25, 0.5, 1, 2 in) = 16 conditions.
- Measured **Movement Time (MT)** for each D–W combination.
- Found:
    - MT ↑ with larger D.
    - MT ↓ with larger W.
    - MT depends on both D and W.
![[Pasted image 20251022063037.png]]
![[Pasted image 20251022063101.png]]
![[Pasted image 20251022063125.png]]

---
## Index of Difficulty (ID)
Combines **distance** and **width** into one measure of **task difficulty**, in **bits**.
### Formula
![[Pasted image 20251022063206.png]]
- Larger **D/W** ratio = higher difficulty.
- Measured in **bits of information**.
### Examples
![[Pasted image 20251022063250.png]]
![[Pasted image 20251022063300.png]]

|D/W|Calculation|ID (bits)|
|---|---|---|
|8|log₂(8 + 1)|3.17|
|4|log₂(4 + 1)|2.32|
|16|log₂(16 + 1)|4.09|
Same **D/W** ratio → same **ID** → same **task difficulty**.

---
## Building a Fitts’ Law Model
### Linear Relationship
![[Pasted image 20251022063330.png]]
- Distance (D): Distance of the target 
- Width (W): width of the target in the direction of the movement 
- ID: index of difficulty of the task, in bits 
- b: rate at which time increases with task difficulty, in seconds/bit 
- a is a time constant, in seconds
### Key Insight
- **a** and **b** depend on the **input device** and **body part** (e.g., mouse, finger, head).
- **D, W, ID** depend on the **task**, not the device.
---
## Speed–Accuracy Trade-Off
- **Fitts’ Law models this trade-off.**
- Moving **faster** → less accuracy.
- Moving **slower** → more accuracy.
- Fundamental to input tasks: pointing, typing, dragging, etc.
---
## 🖱️ Factor of Device
Performance varies with:
- **Motor space movement** (hands, eyes, head).
- **Input device** (mouse, trackpad, joystick).
- **Mapping to display** (control-display gain, CD gain).
### Control–Display (CD) Gain
![[Pasted image 20251022063625.png]]
- **>1:** faster cursor, less precise (coarse).
- **<1:** slower cursor, more precise (fine).
![[Pasted image 20251022063641.png]]
---
## Throughput (TP)
### Definition
Throughput = **efficiency** of information transfer (speed + accuracy).

![[Pasted image 20251022063710.png]]
- ↑ TP → more information transferred per second.
- Combines **speed** (MT) and **accuracy** (ID).
---
## Throughput Examples
- **Mouse:** ~10.4 bits/s
- **Fingers:** up to 40 bits/s (adjacent buttons)
- **Head pointing:** ~4.2 bits/s  
---
## Throughput Fitts' Law Visualisation
![[Pasted image 20251022064140.png]]

---
## Throughput Thought Experiments
### Scenario 1 — Careful, No Errors
![[Pasted image 20251022063936.png]]

|Interface|Bits/Selection|MT|Selections/s|Throughput|
|---|---|---|---|---|
|A|1|250 ms|4|4 bit/s|
|B|4|666 ms|1.5|6 bit/s|
|C|7|1000 ms|1|7 bit/s|
**C highest throughput** (more info per time).

---
### Scenario 2 — Fast, Error-Prone
![[Pasted image 20251022063951.png]]

|Interface|Bits/Selection|Error Rate|MT|Effective TP ↓|
|---|---|---|---|---|
|A|1|0%|250 ms|high|
|B|4|40%|250 ms|moderate|
|C|7|80%|250 ms|low|
**Errors reduce throughput**, even if fast.

---
## Key Takeaways
- **Fitts’ Law**: models aimed movements (pointing, typing, etc.).
- **MT = a + b × ID** — linear relationship.
- **Speed–accuracy trade-off** is inherent in all input.
- **Throughput (ID/MT)** combines both into a single metric of efficiency.
- Device performance can be compared via **throughput**.
---