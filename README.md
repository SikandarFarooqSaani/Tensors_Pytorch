# LangChain & PyTorch: AI Development Foundations

> **Note:** This documentation was AI-generated using a custom prompt to synthesize technical learning modules into a structured, readable format for developers and students. 

---

## 🦜 LangChain: Prompt Engineering & Chat Logic

The primary goal of custom prompts in LangChain is to act as a security layer. By wrapping user inputs, we ensure the user never has direct control over the LLM instructions, preventing prompt injection and maintaining application consistency.

### 🛠 Core Implementations

#### 1. Prompt Templates (`prompt_generator.py`)
Standardizes input formatting with strict validation.
*   **Validation:** Setting `validate_template=True` ensures the app crashes early if an input variable is missing, preventing silent failures.
*   **Serialization:** Templates can be saved as `.json` files to decouple prompt logic from Python code.

#### 2. Interactive UI (`prompt_ui.py`)
A web interface built using **Streamlit** and **ChatGoogleGenerativeAI**.
*   Uses `load_prompt` to dynamically fetch saved templates.
*   Inputs are gathered via `st.selectbox` and passed into an execution chain.

#### 3. Conversational Memory (`chatbot.py` & `message_placeholder.py`)
Implementation of "Stateful" AI that remembers previous messages.
*   **Message Types:** `SystemMessage` (Behavior), `HumanMessage` (User), and `AIMessage` (Response).
*   **Terminal Chat:** A `while True` loop that appends every interaction to a `chat_history` list.
*   **MessagePlaceholders:** Used to inject historical context into a prompt template dynamically, allowing the model to answer follow-up questions effectively.

---

## 🔥 PyTorch: Tensor Fundamentals

A journey into deep learning starts with understanding **Tensors**, the N-dimensional arrays used for all computations in PyTorch.

### 1. Tensor Creation & Hardware
Checking for GPU availability is the first step for high-performance computing.

import torch
device = "cuda" if torch.cuda.is_available() else "cpu"

```python
```
Initializers: empty(), zeros(), ones(), rand().

Reproducibility: torch.manual_seed() ensures random outputs remain consistent across runs.

Identity & Ranges: eye() for identity matrices, linspace() for evenly spaced values, and arange().

2. Operations & Math
Arithmetic: Supports standard +, -, *, /, // (floor), and  (power).

In-place: Functions ending in _ (e.g., .add_()) modify the tensor directly without re-assignment.

Reduction: .sum(), .mean(), .std(), and .argmax() (finds the index of the highest value).

Matrix Math: matmul() for multiplication and transpose() for flipping dimensions.

3. Shape Manipulation
Critical for preparing data (especially images) for neural networks.

Reshaping: flatten(), permute() (reordering axes), and unsqueeze() (adding dimensions for batches).

Cloning: Use .clone() to avoid simple reference copying.

4. Interoperability (The NumPy Bridge)
PyTorch integrates seamlessly with the scientific Python stack.

To NumPy: tensor.numpy()

From NumPy: torch.from_numpy(ndarray)

🚀 Execution & Usage
LangChain UI: streamlit run prompt_ui.py

Terminal Bot: python chatbot.py

Tensor Scripts: Run in any environment with torch installed to see GPU acceleration in action.
```
