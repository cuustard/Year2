---
date: 2025-10-23
noted: true
tags:
  - week3
---
```table-of-contents
```

> [!info] Resources
> [📊 PowerPoint]()
> [📽️Lecture Recording]()

---
## Purpose of Input Models

**Models** help predict and explain user performance with interfaces.
- **Good models** are simple enough to apply but detailed enough to explain key effects.
- **Fitts’ Law** models aimed movements — where the **target is known**, **reachable**, and **movement is continuous** (no searching or discrete steps).

✅ Used for **pointing** tasks (mouse, pen, touch).  
❌ Not suitable for **drawing** or multi-phase movement.

---
## Extending Fitts’ Law to 2D

![[Pasted image 20251024011649.png]]

Now both **X** and **Y** dimensions affect target acquisition.
- **D:** Distance from cursor to target center.
- **W:** Width of the target _along the movement direction_.

Applies to real-world interfaces like **menus**, **buttons**, and **icons**.
![[Pasted image 20251024011723.png]]
Menu designs where targets are large and near the cursor minimize movement time.
![[Pasted image 20251024011745.png]]

---
## Goal-Crossing Model (Crossing vs Pointing)
### Background

- Introduced with **pen/stylus** interfaces (Ren & Moriya, 2000).
- Selection occurs when the pointer **crosses** a target boundary — no click needed.

![[Pasted image 20251024011825.png]]
### Differences

|Pointing|Crossing|
|---|---|
|Stop inside target|Pass through target|
|Correct near end|Correct continuously|
|Requires precise click|Easier with noisy or jittery input|
![[Pasted image 20251024011839.png]]
![[Pasted image 20251024011931.png]]

---
### Advantages of Crossing

Works better for:
- **Thin objects** or **multi-selection** (e.g., swipe gestures).
- **Buttonless devices** (pen, head tracking, mid-air input).
- **Low-precision environments** (tremors, motion noise).
- Supports fluid, continuous interaction (e.g., **Apple QuickPath** keyboard).

![[Pasted image 20251024011948.png]]
#### **Example:**  
Crossing-based actions (left-side menus) are faster than pointing-based ones (tiny search icons).

---
## Fastest Points on the Screen

- **Corners and edges** are easiest to reach since the pointer cannot move past them.
- Placing key elements (menu bars, buttons) in corners enhances accessibility and speed.

---
## Steering Law (Accot–Zhai, 1997)

Describes **movement through constrained paths** (like a tunnel).

![[Pasted image 20251024012043.png]]

- **MT:** Movement Time
- **A & B:** Constant dependent on pointing system
- **D:** Path length (distance).
- **W:** Path width (constraint tolerance).

**Applies to:** navigating menus, sliders, or curved paths.

**Interpretation:**  
Narrow or long tunnels → slower movement.
#### Example Applications

- Moving a cursor through nested menus.
- Dragging through constrained paths (e.g., sliders).
- Steering between adjacent on-screen objects.
![[Pasted image 20251024012212.png]]

---
## Keystroke-Level Model (KLM)

**Purpose:**  
Predict time to complete routine tasks using a combination of physical, mental, and system actions.
### Basic Operators and Times

|Operator|Description|Typical Time|
|---|---|---|
|**K**|Keystroke (letter, key, etc.)|0.12–0.28 s|
|**H**|Homing (hand between devices)|0.4 s|
|**B / BB**|Button press / click|0.1 s / 0.2 s|
|**P**|Point to a target|1.1 s|
|**D(nD, lD)**|Draw nD lines of length lD|0.9·nD + 0.16·lD|
|**M**|Mental preparation (decision/look)|1.35 s|
|**R(t)**|System response|variable|

---
#### Example Task: Convert 12 Euro to USD

![[Pasted image 20251024012319.png]]

Steps:
1. Select text field → `P, B, B`
2. Type “12” → `H, M, K, K`
3. Select “Euro” → `H, M, P, B, B`
4. Select “Dollar” → `M, P, B, B`
5. Press “Convert” → `P, B, B`

**Predicted Time:** ≈ 10.6 seconds

---

### KLM Usefulness

**Advantages:**
- Simple and intuitive.
- Can be done early (even from sketches).
- Accurate for **routine, expert tasks**.
- Great for comparing **UI design alternatives**.

**Limitations:**
- Assumes **expert, error-free** users.
- Not suitable for tasks involving **exploration, reasoning, or learning**.

---
## Key Takeaways

- **Fitts’ Law**: Models aimed movements (distance + size determine time).
- **Crossing Model**: Continuous motion across targets — great for stylus or mid-air input.
- **Steering Law**: Movement constrained by boundaries or obstacles.
- **KLM**: Predicts total task time from component actions.

---