# Testing Approach & Methodology

This document explains the **strategy**, **techniques**, and **reasoning** behind the
thermostat controller test cases.

---

## 1. Objective

Design the *optimal* (effective **and** efficient) set of test cases that fully
exercise the thermostat's heating-decision logic with **minimal redundancy**.

- **Effective** → every decision boundary is covered.
- **Efficient** → no duplicate cases that test the same logic twice.

---

## 2. Understanding the System Under Test

The thermostat decides **Heating ON / OFF** from two inputs:

| Input | Values |
|-------|--------|
| Measured temperature | Any integer (°C) |
| Heating switch | ON / OFF |

The switch position selects **which threshold** applies:

| Switch | Heat OFF when… | Heat ON when… |
|--------|----------------|---------------|
| ON  | temp ≥ `[HIGH]` °C | temp < `[HIGH]` °C |
| OFF | temp ≥ `[LOW]` °C  | temp < `[LOW]` °C  |

> The *"heat off"* range is **inclusive** — the boundary value itself produces OFF.

---

## 3. Techniques Applied

### 🔹 Boundary Value Analysis (BVA)
Defects most often hide at the **edges** of ranges. For each threshold we test the
value **just below**, **at**, and (conceptually) **just above** the boundary. This is
the primary technique used in this project.

### 🔹 Equivalence Partitioning (EP)
Temperatures naturally split into two classes per switch state: *heat on* and
*heat off*. Testing one representative value per class avoids redundant cases.

### 🔹 State Transition Testing
Flipping the switch ON ↔ OFF changes the **active threshold**. Covering both switch
positions confirms the controller selects the correct range for each state.

---

## 4. How the Boundaries Were Derived

1. Read the specification diagram for each switch position.
2. Identify the temperature where the decision flips between ON and OFF.
3. Apply the **inclusive** rule: the boundary value belongs to the *heat off* range.
4. Choose BVA points around each boundary (below the edge, and at the edge).

---

## 5. Why These 4 Cases Are Sufficient

| Case | What it protects against |
|------|--------------------------|
| TC01 | Off-by-one error below the low boundary (switch OFF) |
| TC02 | Wrong inclusive/exclusive handling at the low boundary |
| TC03 | Off-by-one error below the high boundary (switch ON) |
| TC04 | Wrong inclusive/exclusive handling at the high boundary |

Together they cover **both switch states** and **both boundary directions**, which is
exactly where logic defects appear in this type of controller.

---

## 6. Result

✅ **100% score on TestDome.** The chosen set caught all intended boundary conditions
with no redundant cases — meeting the goal of an *effective and efficient* suite.

---

## 7. Exit Criteria

- All boundary cases pass.
- Both switch positions are covered.
- TestDome solution returns **100%**.
