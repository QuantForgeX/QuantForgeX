# 🧩 Contributing to QuantForgeX

Thank you for your interest in contributing to **QuantForgeX**!  
We’re building a transparent, community-driven ecosystem for systematic trading — and your contributions help make it possible.

This document explains how to contribute to our **open Python modules**, which include:
- 📈 **Indicators**  
- ⚙️ **Orchestrator (`run.py`)**  
- 🔧 **Utilities and pipeline components**

---

## 📜 Overview

QuantForgeX maintains a modular approach:
- **Frontend & infrastructure** (UI, servers, platform orchestration) are **closed-source**.  
- **Trading logic and research modules** (Python) are **open for contribution**.

This ensures open innovation in the **research and trading layer** while maintaining platform security and reliability.

---

## 🚀 How You Can Contribute

We welcome contributions that:
1. **Add or improve indicators**  
   - Technical (e.g., EMA, RSI, MACD, ATR, etc.)  
   - Statistical or ML-based (e.g., rolling regressions, AI signals)  
2. **Enhance orchestration logic (`run.py`)**  
   - Improve modularity, efficiency, or real-time compatibility  
3. **Add performance and stability improvements**  
   - Optimize existing functions  
   - Improve backtesting speed or accuracy  
4. **Add testing and validation utilities**  
   - Help ensure strategy robustness and correctness  

If you’re unsure whether an idea fits, open an [issue](../../issues) to discuss before coding.

---

## 🧠 Repository Structure

Typical structure for reference:
```
quantforgex/
│
├── indicators/
│ ├── sma.py
│ ├── ema.py
│ ├── macd.py
│ └── init.py
│
├── orchestrator/
│ ├── run.py
│ ├── utils.py
│ └── pipeline.py
│
└── tests/
└── test_indicators.py
```


You can add your module under the relevant folder (or suggest a new one if justified).

---

## ⚙️ Setup Instructions

1. **Fork** this repository.
2. **Clone** your fork:
   ```bash
   git clone https://github.com/<your-username>/quantforgex.git
   cd quantforgex
   ```
3. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # on Windows: venv\Scripts\activate
   ```
4. Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

5. Run tests to confirm setup:
   ```bash
   pytest
   ```
---
## 🧩 Adding a New Indicator
1. Create a new Python file inside /indicators/ (e.g., rsi.py).
2. Follow the template below:
    ```python
    import pandas as pd
    
    def RSI(series: pd.Series, period: int = 14) -> pd.Series:
        delta = series.diff()
        gain = delta.clip(lower=0).rolling(period).mean()
        loss = -delta.clip(upper=0).rolling(period).mean()
        rs = gain / loss
        return 100 - (100 / (1 + rs))
    ```
3. Add a short docstring describing:
  - The purpose of the indicator
  - Parameters and return value
  - Example usage
4. Add a test case in /tests/test_indicators.py to ensure correctness.
---
## 🧭 Contribution Standards

✅ Follow PEP8
✅ Type hints for all functions
✅ Docstrings for all modules
✅ No data leakage or lookahead bias in indicators
---
## ⚖️ License & Attribution

By contributing, you agree that your submissions are licensed under the MIT License of this repository.

Credit will be given for all accepted contributions in the project’s README and release notes.
