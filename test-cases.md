# Test Cases – Thermostat Controller

These test cases verify the heating-decision logic of a thermostat controller using
**Boundary Value Analysis (BVA)**. The *"heat off"* range is **inclusive** of its
boundary value (the boundary temperature itself results in heating OFF).

> **Note:** Replace the bracketed values `[LOW]` and `[HIGH]` with the exact boundary
> temperatures from your verified TestDome solution.

---

## Inputs & Output

| Field | Type | Values |
|-------|------|--------|
| **Measured temperature** | Number (°C) | Any integer |
| **Heating switch** | Boolean | ON / OFF |
| **Heating** (expected output) | Boolean | ON / OFF |

---

## Test Case TC01 — Below low boundary (Switch OFF)

| Attribute | Value |
|-----------|-------|
| **Test ID** | TC01 |
| **Title** | Heating turns ON just below the low boundary (switch OFF) |
| **Technique** | Boundary Value Analysis |
| **Preconditions** | Heating switch is **OFF** |
| **Input – Temperature** | `[LOW] - 1` °C |
| **Input – Switch** | OFF |
| **Expected – Heating** | **ON** |
| **Result** | ✅ Pass |

**Brief analysis:** Just below the low threshold, the room is too cold, so heating
must turn ON even though the switch is in the OFF (frost-protection) position.

---

## Test Case TC02 — At low boundary, inclusive (Switch OFF)

| Attribute | Value |
|-----------|-------|
| **Test ID** | TC02 |
| **Title** | Heating stays OFF exactly at the low boundary (inclusive) |
| **Technique** | Boundary Value Analysis |
| **Preconditions** | Heating switch is **OFF** |
| **Input – Temperature** | `[LOW]` °C |
| **Input – Switch** | OFF |
| **Expected – Heating** | **OFF** |
| **Result** | ✅ Pass |

**Brief analysis:** The boundary value itself falls inside the *"heat off"* range
because it is **inclusive**. This is the most defect-prone case and must be tested.

---

## Test Case TC03 — Below high boundary (Switch ON)

| Attribute | Value |
|-----------|-------|
| **Test ID** | TC03 |
| **Title** | Heating turns ON just below the high boundary (switch ON) |
| **Technique** | Boundary Value Analysis |
| **Preconditions** | Heating switch is **ON** |
| **Input – Temperature** | `[HIGH] - 1` °C |
| **Input – Switch** | ON |
| **Expected – Heating** | **ON** |
| **Result** | ✅ Pass |

**Brief analysis:** With the switch ON, the target range is higher. Just below the
high threshold, heating must remain ON to reach the target temperature.

---

## Test Case TC04 — At high boundary, inclusive (Switch ON)

| Attribute | Value |
|-----------|-------|
| **Test ID** | TC04 |
| **Title** | Heating stays OFF exactly at the high boundary (inclusive) |
| **Technique** | Boundary Value Analysis |
| **Preconditions** | Heating switch is **ON** |
| **Input – Temperature** | `[HIGH]` °C |
| **Input – Switch** | ON |
| **Expected – Heating** | **OFF** |
| **Result** | ✅ Pass |

**Brief analysis:** At the high boundary value, the target is reached, so heating
turns OFF. Because the *"heat off"* range is inclusive, the boundary value yields OFF.

---

## Summary Table

| # | Temperature | Switch | Expected Heating | Technique | Result |
|---|-------------|--------|------------------|-----------|--------|
| TC01 | `[LOW] - 1` °C  | OFF | ON  | BVA | ✅ |
| TC02 | `[LOW]` °C      | OFF | OFF | BVA | ✅ |
| TC03 | `[HIGH] - 1` °C | ON  | ON  | BVA | ✅ |
| TC04 | `[HIGH]` °C     | ON  | OFF | BVA | ✅ |

**Overall result:** 4/4 passed — **100% on TestDome.**
