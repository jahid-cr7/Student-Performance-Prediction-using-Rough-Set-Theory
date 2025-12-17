# Rough Set Theory for Student Performance Prediction

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Machine Learning](https://img.shields.io/badge/ML-Rough%20Set%20Theory-orange.svg)](https://en.wikipedia.org/wiki/Rough_set)

A comprehensive implementation of **Rough Set Theory** applied to student performance prediction using the UCI Student Performance Dataset. This project demonstrates how attribute reduction (reduct) can improve classification accuracy while reducing computational complexity.

## 📋 Table of Contents

- [Features](#features)
- [About Rough Set Theory](#about-rough-set-theory)
- [Installation](#installation)
- [Usage](#usage)
- [Results](#results)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)

## ✨ Features

- **Rough Set Attribute Reduction**: Automatically identifies the minimal set of features (reduct) that preserve classification accuracy
- **Decision Rule Generation**: Extracts interpretable if-then rules from the decision table
- **Performance Comparison**: Compares baseline (all features) vs. reduct-based models
- **Comprehensive Metrics**: Provides accuracy, precision, recall, F1-score, and confusion matrices
- **Automatic Dataset Handling**: Downloads dataset automatically or uses local files
- **Educational Focus**: Designed for CS0447 (Computer Organization) course project

## 🎓 About Rough Set Theory

Rough Set Theory, introduced by Zdzisław Pawlak, is a mathematical framework for:
- **Handling uncertainty** in data analysis
- **Attribute reduction** (finding minimal feature sets)
- **Rule extraction** from decision tables
- **Lower and upper approximations** of sets

In this project, we demonstrate how reducing attributes from 11 to 5 features can **improve accuracy** (typically 82% → 84%+) while reducing memory usage and computational overhead—perfect for low-level system optimization concepts in Computer Organization courses.

## 🚀 Installation

### Prerequisites

- Python 3.8 or higher
- pip package manager

### Step 1: Clone the Repository

```bash
git clone https://github.com/Zonaid007/rough-set-student-performance.git
cd rough-set-student-performance
```

### Step 2: Install Dependencies

```bash
pip install -r requirements.txt
```

Or install manually:

```bash
pip install pandas numpy scikit-learn
```

## 📖 Usage

### Basic Usage

Simply run the main script:

```bash
python zedd_rough-learn.py
```

The script will:
1. Attempt to download the UCI Student Performance dataset automatically
2. If download fails, it will use `student-mat.csv` from the current directory
3. If no local file exists, it generates synthetic data for demonstration

### Using Your Own Dataset

Place your `student-mat.csv` file in the project root directory. The script will automatically detect and use it.

### Expected Output

```
Loading UCI Student Performance Dataset...
Dataset loaded: 395 samples, 33 attributes

Preprocessing data...
Target distribution: Counter({0: 219, 1: 176})

============================================================
SCENARIO A: ALL ATTRIBUTES (Baseline)
============================================================
Features used: 11
Accuracy: 84.81%

============================================================
SCENARIO B: ROUGH SET REDUCT (Feature Selection)
============================================================
Features used: 5
Accuracy: 86.08%
Selected Reduct: ['studytime', 'failures', 'G2', 'absences', 'famsup']

============================================================
DECISION RULE GENERATION
============================================================
Top Decision Rules (from Reduct Features):
Rule 1: IF studytime = High AND failures = 0 AND G2 = High THEN Good Performance...
...
```

## 📊 Results

### Typical Performance Improvement

- **Baseline (11 features)**: ~82-85% accuracy
- **Reduct (5 features)**: ~84-87% accuracy
- **Improvement**: +1-3% accuracy
- **Feature Reduction**: 54.5% fewer attributes

### Key Findings

1. **Reduced Complexity**: 5 features achieve better or equal performance than 11 features
2. **Interpretability**: Decision rules are more understandable with fewer attributes
3. **Efficiency**: Lower memory footprint and faster training/inference
4. **Selected Reduct Features**:
   - `studytime`: Time spent studying per week
   - `failures`: Number of past class failures
   - `G2`: Second period grade
   - `absences`: Number of school absences
   - `famsup`: Family educational support

## 📁 Project Structure

```
rough-set-student-performance/
│
├── zedd_rough-learn.py      # Main implementation script
├── README.md                # This file
├── requirements.txt         # Python dependencies
├── .gitignore              # Git ignore rules
├── LICENSE                 # MIT License
│
├── dataset/                # Dataset folder (optional)
│   └── student-mat.csv     # UCI Student Performance dataset
│
└── results/                # Output folder (generated)
    └── (classification reports, rules, etc.)
```

## 🔬 How It Works

### 1. Data Preprocessing
- Loads UCI Student Performance dataset
- Encodes categorical variables
- Creates binary target: `performance` (Good ≥ 10, Poor < 10)

### 2. Rough Set Reduct Calculation
- Calculates dependency of decision attribute on condition attributes
- Identifies minimal attribute set that preserves classification capability
- Removes redundant features while maintaining accuracy

### 3. Model Training
- Trains Random Forest classifier on:
  - **Scenario A**: All 11 features (baseline)
  - **Scenario B**: 5 reduct features (optimized)

### 4. Decision Rule Generation
- Discretizes continuous features into bins (Low/Medium/High)
- Groups by feature combinations
- Extracts if-then rules with support and confidence metrics

### 5. Evaluation
- Compares accuracy between scenarios
- Generates classification reports
- Displays confusion matrices

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request. Here are some ways you can contribute:

1. **Improve Rough Set Algorithm**: Implement more sophisticated reduct calculation methods
2. **Add Visualizations**: Create plots for feature importance, rule visualization, etc.
3. **Support More Datasets**: Extend to work with other classification datasets
4. **Performance Optimization**: Optimize code for larger datasets
5. **Documentation**: Improve code comments and documentation

### Contribution Guidelines

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**Zonaid007**

- GitHub: [@Zonaid007](https://github.com/Zonaid007)
- Project Link: [https://github.com/Zonaid007/rough-set-student-performance](https://github.com/Zonaid007/rough-set-student-performance)

## 🙏 Acknowledgments

- UCI Machine Learning Repository for the Student Performance dataset
- Zdzisław Pawlak for developing Rough Set Theory
- The open-source community for excellent Python libraries (pandas, scikit-learn, numpy)

## 📚 References

- [Rough Set Theory - Wikipedia](https://en.wikipedia.org/wiki/Rough_set)
- [UCI Student Performance Dataset](https://archive.ics.uci.edu/ml/datasets/Student+Performance)
- Pawlak, Z. (1982). "Rough sets". International Journal of Computer & Information Sciences. 11 (5): 341–356.

## 💡 Use Cases

This project can be used for:

- **Academic Projects**: CS0447, Machine Learning, Data Mining courses
- **Research**: Feature selection, attribute reduction studies
- **Education**: Learning Rough Set Theory concepts
- **Portfolio**: Demonstrating ML and data science skills
- **Optimization**: Understanding memory-efficient ML approaches

---

⭐ If you find this project helpful, please give it a star on GitHub!

#   S t u d e n t - P e r f o r m a n c e - P r e d i c t i o n - u s i n g - R o u g h - S e t - T h e o r y  
 