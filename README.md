# Boolean Truth Table Generator

An AI-powered web application that converts **natural-language Boolean logic problem statements into truth tables** using a custom-trained machine learning model.

The goal of this project is to make Boolean logic easier to work with by allowing users to describe a logical problem in plain English instead of manually constructing Boolean expressions and truth tables.

---

## 🚀 Overview

Given a problem statement such as:

> "A security system activates when the door is closed and either the password is correct or the administrator overrides the system."

The system analyzes the statement, identifies the logical variables and relationships, and generates the corresponding Boolean truth table.

### Input

A natural-language problem statement.

```text
A light turns on when the switch is pressed and the power is available.
```

### Output

The system identifies the variables:

```text
S = Switch
P = Power
```

and generates the corresponding Boolean expression and truth table.

---

## ✨ Features

* 🧠 **Custom-trained AI model**
* 📝 Natural-language problem statement input
* 🔢 Automatic identification of Boolean variables
* 🔀 Boolean expression generation
* 📊 Automatic truth-table generation
* ⚡ Fast inference through a web interface
* 🎨 Interactive and user-friendly UI
* 🔍 Clear representation of intermediate results
* 🧩 Designed for Boolean logic and digital-circuit problems

---

## 🏗️ System Architecture

The application consists of three major components:

```text
                 ┌──────────────────────┐
                 │      User Input      │
                 │                      │
                 │  Problem Statement   │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │     Web Frontend     │
                 │                      │
                 │  Input / Results UI  │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │      Backend API     │
                 │                      │
                 │     FastAPI          │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │   Custom AI Model    │
                 │                      │
                 │ Problem → Logic      │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │   Logic Processing   │
                 │                      │
                 │ Expression → Table   │
                 └──────────┬───────────┘
                            │
                            ▼
                 ┌──────────────────────┐
                 │     Truth Table      │
                 └──────────────────────┘
```

---

## 🔄 How It Works

The complete pipeline is:

```text
Problem Statement
        ↓
Text Preprocessing
        ↓
Custom-Trained Model
        ↓
Boolean Variables
        ↓
Boolean Expression
        ↓
Logic Evaluation
        ↓
Truth Table
        ↓
Frontend Visualization
```

### Example

Input:

```text
The alarm is activated if the door is open and the system is armed.
```

The model may identify:

```text
D = Door Open
A = System Armed
```

Boolean expression:

```text
F = D · A
```

Truth table:

| D | A | F |
| - | - | - |
| 0 | 0 | 0 |
| 0 | 1 | 0 |
| 1 | 0 | 0 |
| 1 | 1 | 1 |

---

## 🤖 Machine Learning Model

This project uses a **custom-trained model** rather than relying entirely on a third-party LLM.

The model is trained to understand Boolean-logic-oriented natural language and convert it into a structured representation that can be evaluated by the logic engine.

### Model Pipeline

```text
Natural Language
       ↓
Tokenization
       ↓
Model
       ↓
Logical Structure
       ↓
Boolean Expression
```

The exact model architecture and training procedure can be found in the `model/` directory.

---

## 🧠 Logic Engine

The model is responsible for understanding the problem statement, while deterministic logic processing is used to generate the final truth table.

This separation is intentional:

```text
AI Model
   │
   │ Understands the problem
   ▼
Boolean Expression
   │
   │ Deterministic evaluation
   ▼
Truth Table
```

This makes the final truth-table generation reproducible and easier to verify.

---

## 📁 Project Structure

A recommended project structure is:

```text
boolean-truth-table-generator/
│
├── frontend/
│   ├── src/
│   ├── public/
│   ├── package.json
│   └── ...
│
├── backend/
│   ├── app/
│   │   ├── main.py
│   │   ├── routes/
│   │   ├── services/
│   │   ├── models/
│   │   └── utils/
│   │
│   ├── requirements.txt
│   └── ...
│
├── model/
│   ├── checkpoints/
│   ├── tokenizer/
│   ├── inference.py
│   └── ...
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── ...
│
├── training/
│   ├── train.py
│   ├── evaluate.py
│   └── ...
│
├── tests/
│
├── docs/
│
├── .gitignore
├── README.md
└── LICENSE
```

---

## 🛠️ Tech Stack

### Frontend

* React
* TypeScript
* Vite
* CSS / Tailwind CSS

### Backend

* Python
* FastAPI
* Pydantic
* Uvicorn

### Machine Learning

* Python
* PyTorch / TensorFlow
* Custom-trained model
* Custom tokenizer / preprocessing pipeline

### Logic Processing

* Boolean expression parser
* Truth-table generator
* Optional symbolic mathematics libraries

---

## ⚙️ Installation

### 1. Clone the repository

```bash
git clone https://github.com/<username>/<repository>.git
cd boolean-truth-table-generator
```

---

### 2. Set up the backend

```bash
cd backend

python -m venv .venv
```

Activate the environment.

#### Linux / macOS

```bash
source .venv/bin/activate
```

#### Windows

```bash
.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Start the server:

```bash
uvicorn app.main:app --reload
```

The API will be available at:

```text
http://localhost:8000
```

---

### 3. Set up the frontend

Open another terminal:

```bash
cd frontend
npm install
npm run dev
```

The frontend will normally be available at:

```text
http://localhost:5173
```

---

## 🔌 API

### Generate Truth Table

```http
POST /api/generate
```

### Request

```json
{
  "problem": "The light turns on when the switch is pressed and power is available."
}
```

### Response

```json
{
  "variables": [
    "S",
    "P"
  ],
  "expression": "S AND P",
  "truth_table": [
    {
      "S": 0,
      "P": 0,
      "output": 0
    },
    {
      "S": 0,
      "P": 1,
      "output": 0
    },
    {
      "S": 1,
      "P": 0,
      "output": 0
    },
    {
      "S": 1,
      "P": 1,
      "output": 1
    }
  ]
}
```

---

## 📊 Truth Table Generation

For `n` Boolean variables, the system generates:

```text
2ⁿ
```

possible input combinations.

For example, with three variables:

```text
2³ = 8
```

combinations are generated.

```text
A B C | F
------+---
0 0 0 | ?
0 0 1 | ?
0 1 0 | ?
0 1 1 | ?
1 0 0 | ?
1 0 1 | ?
1 1 0 | ?
1 1 1 | ?
```

The Boolean expression is evaluated for every combination to produce the final output.

---

## 🧪 Testing

Run the test suite using:

```bash
pytest
```

Tests should cover:

* Natural-language parsing
* Variable extraction
* Boolean expression generation
* AND / OR / NOT operations
* Nested expressions
* Truth-table generation
* Invalid inputs
* Model inference
* API endpoints

Example:

```text
Input:
A and B

Expected:
F = A AND B
```

---

## 📈 Model Evaluation

The model can be evaluated using metrics such as:

* Expression accuracy
* Variable extraction accuracy
* Logical structure accuracy
* Exact-match accuracy
* Truth-table accuracy

The most important metric for the final application is:

> **Truth-table correctness**

because a syntactically valid expression is not necessarily logically correct.

---

## ⚠️ Limitations

The model may have difficulty with:

* Ambiguous natural language
* Statements containing implicit conditions
* Very long problem descriptions
* Unusual logical terminology
* Multiple interpretations of the same statement
* Statements requiring domain-specific assumptions

For this reason, the application should clearly display the generated Boolean expression before or alongside the final truth table.

---

## 🔮 Future Improvements

Possible future improvements include:

* [ ] Boolean expression visualization
* [ ] Karnaugh map generation
* [ ] Canonical SOP/POS generation
* [ ] Logic circuit generation
* [ ] NAND/NOR-only circuit conversion
* [ ] Circuit diagram visualization
* [ ] Step-by-step reasoning/explanation
* [ ] Model confidence estimation
* [ ] Support for more complex logical statements
* [ ] Dataset expansion
* [ ] Model fine-tuning
* [ ] User feedback for incorrect predictions
* [ ] Export truth tables as CSV/PDF
* [ ] Interactive circuit simulation

---

## 🎯 Project Goal

The long-term goal of this project is to create an intelligent **Boolean Logic Assistant** capable of converting natural-language digital-logic problems into structured digital logic.

The envisioned pipeline is:

```text
Natural Language
       ↓
AI Understanding
       ↓
Boolean Expression
       ↓
Truth Table
       ↓
K-Map
       ↓
Simplified Expression
       ↓
Logic Circuit
       ↓
Circuit Simulation
```

This would allow users to go from a **problem statement to a complete digital logic implementation** using a single interface.

---

## 👨‍💻 Author

**Navaneeth V**

B.Tech CSE
Indian Institute of Technology Hyderabad

---

## 📄 License

This project is licensed under the MIT License.

See [`LICENSE`](LICENSE) for more information.
