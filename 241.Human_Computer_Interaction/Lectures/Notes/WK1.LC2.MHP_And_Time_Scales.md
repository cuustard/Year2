> [!info] Resources
> [📊 PowerPoint](WK1.LC2.MHP_And_Time_Scales.pdf)
> [📽️Lecture Recording](https://lancaster.cloud.panopto.eu/Panopto/Pages/Viewer.aspx?id=a4f564d6-17b3-4eda-8be0-b36400345d97)

---
## Humans as Information Processors
Humans process information in **three main stages**:
1. **Perception** – Receiving information through sensory organs (eyes, ears, etc.).
2. **Cognition** – Interpreting, processing, and deciding based on experience and memory.
3. **Motor Action** – Producing output (e.g., speaking, typing, moving).

Similar to computers: input → processing → output.  
We can attempt to **predict human performance** like computer performance (e.g., using cycle times).

---
## Model Human Processor (MHP)
A theoretical model (Card, Moran, and Newell, 1983) describing human information processing in HCI.
### Structure
The model has **three interacting subsystems**:

|Subsystem|Components|Function|
|---|---|---|
|**Perceptual**|Perceptual memory + perceptual processor|Transforms external stimuli into mental symbols|
|**Cognitive**|Working memory, long-term memory, cognitive processor|Interprets and decides actions|
|**Motor**|Motor processor + effectors (hands, fingers, etc.)|Executes physical actions|
## Perceptual System
### Perceptual Memory (Buffer)
- Temporarily stores sensory data before processing.
    - **Visual store:** ~200 ms
    - **Auditory store:** ~1500 ms
- Holds **raw data** (low-level features).
- Buffers data to allow for recognition and integration.
### Perceptual Processor
- Encodes sensory input into symbolic form.
- **Cycle time (Tₚ):** ~100 ms
    - Shorter for intense or “pop-out” stimuli.
```
Bloch’s Law: R = I × t  → perception integrates stimuli over short intervals.
```
- Can’t encode everything before new input arrives.
- Influenced by **attention**, **Gestalt patterns**, and **associations**.
---
## Cognitive System
### Cognitive Processor
- Works with **symbolic information** from working memory.
- Operates via **recognize–act cycles**:
    1. **Recognize:** activate related knowledge in long-term memory.
    2. **Act:** decide next step → update working memory.
- **Cycle time (T𝒸):** ~70 ms
    - Decision time ↑ with uncertainty.
    - Decreases with **practice** and **motivation**.
- Recognition = **parallel**, Acting = **serial** (one at a time)

![[Pasted image 20251019125340.png]]
---
## Motor System
### Function
- Converts decisions into physical actions.
- **Cycle time (Tₘ):** 30–100 ms (avg ~70 ms).
### Example
- Typist at 120 wpm ≈ 9.4 characters/sec → ~106 ms/character.
- Finger-down/finger-up ≈ 53 ms.
### Pen-Stroke Experiment
- Draw back and forth between two lines for 5 seconds.
- ~10 strokes/sec → ~100 ms per stroke.
- Correction time ≈ **250 ms** (100 + 70 + 70).
![[Pasted image 20251019125134.png]]

---
## Reaction Time Example
Sequence for pressing a button after a prompt:
1. **Perceive stimulus** (Perceptual Processor)
2. **Recognize and decide** (Cognitive Processor)
3. **Press button** (Motor Processor)

→ Total reaction time ≈ **240 ms** (100 + 70 + 70).

---
## Time Scales of Human Action

|Scale|Type of Activity|Time Range|
|---|---|---|
|Neural firing|1 ms||
|Perceptual & motor actions|100 ms||
|Cognitive decisions|1 s||
|Task steps|10 s||
|Complex goals / planning|minutes–hours||
|Life activities|years–lifetime|
![[Pasted image 20251019125223.png]]
## Human Response Time Requirements in HCI

|Deadline|Function|Design Implication|
|---|---|---|
|0.001 s|Detect silent audio gap|Max drop-out in audio feedback|
|0.01 s|Notice pen lag|Max lag in stylus interfaces|
|0.1 s|Hand–eye feedback|Feedback for mouse or click|
|1 s|Conversational gap|Show progress or waiting indicator|
|10 s|Focus retention|Allow one task step before distraction|
|100 s|Critical decisions|All info must be available within this time|
**System responsiveness:**
- <0.01 s → real-time control
- <1 s → user feels in control
- > 10 s → frustration, memory decay
![[Pasted image 20251019125247.png]]
## Key Takeaways
- The **MHP** models human performance in HCI.
- Humans can be treated as **information processors** with measurable cycle times.
- Reaction and action times depend on **perceptual, cognitive, and motor** limits.
- **Responsiveness** in interfaces must align with human time scales for effective design.
---
