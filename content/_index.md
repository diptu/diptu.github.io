---
title: "Nazmul Alam Diptu"
date: 2026-07-03
draft: false
---

## Research Summary

My research focuses on the theoretical foundations of KV cache compression in transformer inference — understanding when and why attention memory is compressible, and designing methods with provable guarantees rather than purely empirical heuristics.

I bring a background in production ML systems and software engineering to this transition into theoretical machine learning research, including:

- Provable memory-efficient transformer methods
- Low-rank and sparse attention mechanisms
- Information-theoretic limits of KV cache usage
- Scalable long-context inference algorithms

I'm currently building this foundation independently while preparing to apply to PhD programs.

---

## Publications

**[End-to-End OCR Using Synthetic Dataset Generation for Noisy Conditions](https://doi.org/10.1007/978-981-15-3607-6_41)**
International Joint Conference on Computational Intelligence, 2020
- Deep learning OCR system using synthetic dataset generation
- Improved robustness in low-quality image conditions

**[Population Estimation of Rohingya Refugees Using Artificial Neural Networks](https://doi.org/10.1142/S2196888819500246)**
Vietnam Journal of Computer Science, 2019
- ANN-based population estimation model using satellite and data-driven signals

**[Early Detection of Glaucoma Using Fuzzy Logic in Bangladesh Context](https://doi.org/10.1109/IS.2018.8710490)**
International Conference on Intelligent Systems, 2018
- Fuzzy logic-based diagnostic model for healthcare decision support

---

## Current Research

**Theoretical KV Cache Compression & Efficient Transformers** — independent, ongoing

I'm studying the mathematical foundations of attention and KV cache memory, guided by one question: does this concept help explain or reduce memory cost in transformer inference? Concretely, I'm:

- Building structured notes on linear algebra, probability, and information theory as they apply to attention mechanisms
- Analyzing modern efficient-attention and cache-management methods ([FlashAttention](https://arxiv.org/abs/2205.14135), [PagedAttention](https://arxiv.org/abs/2309.06180), [SnapKV](https://arxiv.org/abs/2404.14469), [KIVI](https://arxiv.org/abs/2402.02750), [H2O](https://arxiv.org/abs/2306.14048), [StreamingLLM](https://arxiv.org/abs/2309.17453)) for their theoretical structure, not just their engineering
- Formulating open questions at the intersection of information theory and long-context inference

**Open questions I'm exploring:**
- Is there a principled information-theoretic lower bound on KV cache size for a given generation-quality tolerance — and how close do heuristics like [H2O](https://arxiv.org/abs/2306.14048), [SnapKV](https://arxiv.org/abs/2404.14469), and [KIVI](https://arxiv.org/abs/2402.02750) come to it?
- Can attention redundancy across layers and heads be characterized precisely enough (via low-rank or sparse structure) to design compression methods with provable reconstruction guarantees, rather than empirically-tuned thresholds?
- Does KV cache compression trade off against long-context reasoning quality fundamentally, or can structure-aware compression preserve long-range dependencies without loss in practice?

---

## Education

**[North South University](https://www.northsouth.edu/)**  
Bachelor of Science in Computer Science and Engineering  
Jan 2015 – Dec 2018  
CGPA: 3.62 / 4.00

**Merit Scholarship:** 25% tuition scholarship awarded based on academic performance

**Focus Areas (Relevant Coursework Exposure):**  
- Data Structures & Algorithms  
- Database Systems  
- Machine Learning Foundations  
- Programming (C, Java, Web Technologies)  
- Probability & Statistics (course-level exposure)

---

## Professional Experience

### Freelance ML & Systems Engineer
**Remote | May 2025 – Present**
- Built AI-based carbon accounting platform ([CarbonIQ](https://github.com/diptu/CarbonIQ/))
- Designed scalable ML pipelines for time-series forecasting
- Implemented FastAPI + PostgreSQL multi-tenant backend architecture
- Designed ETL/ELT workflows using Airflow and dbt
- Deployed containerized ML systems using Docker

---

### Lab Instructor
**[North South University](https://www.northsouth.edu/) | May 2019 – May 2025**
- Taught C, Java, Data Structures, Databases, and Web Technologies
- Mentored students in programming and algorithmic thinking
- Assisted in lab-based problem solving and coursework evaluation

---

### Junior Data Scientist
**[Me-Solshare Ltd](https://solshare.com/) | Nov 2019 – Aug 2021**
- Developed CNN-based time-series forecasting models
- Achieved ~95% accuracy in energy consumption prediction
- Supported decision-making for cost optimization in energy systems

---

### Other Professional Experience

<div class="appendix-section">

- **Product Analyst**, [Power Ledger Pty Ltd](https://powerledger.io/) — Oct 2022 – Feb 2024
- **Technical Analyst**, [InsideMaps Inc](https://www.insidemaps.com/) — Aug 2021 – Jun 2023
- **Intern**, [Grameenphone Limited](https://www.grameenphone.com/) — May 2019 – Aug 2019

</div>

---

## Technical Skills

### Machine Learning
- PyTorch
- TensorFlow
- scikit-learn

### Programming
- Python
- C / C++
- JavaScript / TypeScript
- Java
- PHP

### MLOps & Systems
- FastAPI
- PostgreSQL / MySQL / MongoDB
- Docker / Docker Compose
- Airflow
- MLflow
- GitHub Actions

<div class="appendix-section">

### Data & Analytics
- SQL
- BigQuery
- Tableau
- Looker Studio

### Tools
- Git, Linux, LaTeX, Markdown
- VS Code, Jupyter, Colab

</div>

---

## Preparation

<div class="appendix-section">

**Papers currently studying:**
- [Attention Is All You Need](https://arxiv.org/abs/1706.03762)
- [FlashAttention](https://arxiv.org/abs/2205.14135) / [FlashAttention-2](https://arxiv.org/abs/2307.08691)
- [Multi-Query Attention (MQA)](https://arxiv.org/abs/1911.02150)
- [Grouped-Query Attention (GQA)](https://arxiv.org/abs/2305.13245)
- [PagedAttention](https://arxiv.org/abs/2309.06180)
- [SnapKV](https://arxiv.org/abs/2404.14469)
- [KIVI](https://arxiv.org/abs/2402.02750)
- [H2O](https://arxiv.org/abs/2306.14048)
- [StreamingLLM](https://arxiv.org/abs/2309.17453)

**Mathematical foundations:**
- Linear Algebra (Strang)
- Statistics (Freedman)
- Probability Theory (in progress)
- Numerical Linear Algebra (Trefethen & Bau, planned)
- Information Theory (Cover & Thomas, planned)
- Optimization Theory (Boyd & Vandenberghe, planned)

</div>
