# 🌡️ Thermostat Controller – QA Test Cases (Boundary Value Analysis)

> A black-box test design for a **thermostat controller**, built with
> **Boundary Value Analysis**, **Equivalence Partitioning**, and
> **State Transition Testing**. Solved on TestDome with a **100% score**.

![Score](https://img.shields.io/badge/TestDome-100%25-brightgreen)
![Technique](https://img.shields.io/badge/Technique-Boundary%20Value%20Analysis-blue)
![Testing](https://img.shields.io/badge/Type-Black%20Box-lightgrey)
![License](https://img.shields.io/badge/License-MIT-green)

---

## 📋 Overview

The system under test is a **thermostat controller** that decides whether to turn
**heating ON or OFF** based on two inputs:

| Input | Description |
|-------|-------------|
| **Measured temperature** | The current temperature, in °C |
| **Heating switch** | A manual switch: ON or OFF |

The expected output is a single decision: **Heating ON / OFF**. The temperature
thresholds differ depending on the switch position, and the *"heat off"* range is
**inclusive** of its boundary value.

---

## 🎯 What Is Tested

- Correct heating decision **at** and **around** each temperature boundary
- Behaviour for both **switch ON** and **switch OFF** ranges
- Inclusive boundary handling ("heat off" includes the boundary value)
- Representative values inside each equivalence class

---

## 🧪 Techniques Used

| Technique | Why It Was Used |
|-----------|-----------------|
| **Boundary Value Analysis (BVA)** | Defects cluster at range edges; tests values just below, at, and just above each threshold |
| **Equivalence Partitioning (EP)** | Groups temperatures into "heat on" / "heat off" classes to avoid redundant cases |
| **State Transition Testing** | Verifies that flipping the switch ON ↔ OFF changes the active threshold correctly |

---

## ✅ Test Cases

The full, formatted test cases live in **[test-cases.md](test-cases.md)**.

| # | Measured Temp | Switch | Expected Heating | Type |
|---|---------------|--------|------------------|------|
| TC01 | Boundary (low edge) | OFF | ON | BVA |
| TC02 | Boundary value (inclusive) | OFF | OFF | BVA |
| TC03 | Boundary (high edge) | ON | ON | BVA |
| TC04 | Boundary value (inclusive) | ON | OFF | BVA |

➡️ See **[test-cases.md](test-cases.md)** for full inputs, steps, and expected results.
➡️ See **[analysis.md](analysis.md)** for the methodology and reasoning.

---

## 📊 Results

✅ **100% score on TestDome.**

The boundary set proved **effective** (all decision edges covered) and **efficient**
(no redundant cases).

---

## 📂 Repository Structure

```
thermostat-testdome-qa/
├── README.md          # Project overview (this file)
├── LICENSE            # MIT License
├── test-cases.md      # 4 formatted test cases
└── analysis.md        # Testing approach & methodology
```

---

## 🚀 How to Use

1. Read **[analysis.md](analysis.md)** to understand the testing approach.
2. Open **[test-cases.md](test-cases.md)** to see the executable test cases.
3. Each case lists the **inputs** (temperature + switch) and the **expected output**.

---

## 🌍 Open Source

This project is **open source** under the **[MIT License](LICENSE)**, which means
anyone is free to use, copy, modify, and share it — including for their own learning
or portfolios — as long as the original license notice is kept.

### 🤝 Contributing

Contributions are welcome! To suggest improvements:

1. **Fork** this repository.
2. Create a branch: `git checkout -b improve-test-cases`
3. Make your changes (e.g. add edge cases, fix a typo, improve docs).
4. **Commit** and **push** your branch.
5. Open a **Pull Request** describing your change.

You can also open an **Issue** to report a problem or propose an idea.

---

## 🔗 References & Links

- 🧩 **Source question:** [TestDome – Thermostat (QA)](https://www.testdome.com/library?skillArea=78&questionId=137821)
- 🌐 **Portfolio:** [aysuismayil.github.io](https://aysuismayil.github.io)
- 🐙 **GitHub:** [github.com/aysuismayil](https://github.com/aysuismayil)
- 💼 **LinkedIn:** _add your LinkedIn URL here_
- ▶️ **YouTube:** _add your YouTube URL here_

---

### 👩‍💻 About Me

**Aysu Ismayilzada** — QA Engineer with 5+ years of experience. I apply a
**Shift Left** approach and take **ownership of quality** from day one.
