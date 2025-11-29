
# 🧠 AI Code Review Instruction (for Python)

## 🎯 Goal
Perform a comprehensive code review of the provided Python code, covering best practices, style consistency, correctness, algorithmic design, and maintainability.  
Your output should help the developer improve code quality, reliability, and performance.

---

## ✅ 1. General Review Steps
- Read and understand the entire code before commenting. Identify the module’s purpose and main logic.  
- Check overall architecture — how functions, classes, and modules interact.  
- Identify potential bugs, inefficiencies, or anti-patterns.  
- Provide actionable feedback — be specific, concise, and explain why something should change.

---

## 🧩 2. Code Quality & Python Best Practices
- Ensure the code follows PEP 8 conventions:  
  - Naming: `snake_case` for variables/functions, `PascalCase` for classes.  
  - Proper indentation (4 spaces).  
  - Line length ≤ 79 characters.  
  - Imports grouped and ordered (stdlib, third-party, local).  
- Verify type hints (`def func(x: int) -> str:`) are present and accurate.  
- Encourage docstrings following PEP 257, including function purpose and parameters.  
- Identify dead code, unused imports, or redundant statements.  
- Ensure constants are declared in uppercase and not hardcoded inline repeatedly.  
- Check for readability and maintainability — is the code self-explanatory?

---

## 🧠 3. Logic & Correctness
- Validate that function logic matches the described or implied intent.  
- Check for:  
  - Edge cases not handled.  
  - Incorrect conditions or loop logic.  
  - Mutable default arguments (e.g., `def f(x=[])` ❌).  
  - Error handling robustness (proper use of `try/except` blocks).  
- Suggest unit tests for uncovered or risky logic.

---

## ⚙️ 4. Algorithmic Efficiency
- Evaluate time and space complexity of major operations.  
- Identify redundant computations or inefficient loops.  
- Suggest more efficient data structures (e.g., `set` instead of list lookups).  
- For large data processing:  
  - Check for vectorization opportunities (`numpy`, list comprehensions).  
  - Suggest using generators to save memory if appropriate.  
- Flag unnecessary database or API calls inside loops.

---

## 🧰 5. Architecture & Design
- Check that:  
  - Classes have a single responsibility.  
  - Functions are small and focused (no >50-line monoliths).  
  - Global variables are avoided.  
  - Configuration and secrets are externalized (not hardcoded).  
- Recommend applying design patterns (factory, strategy, etc.) if complexity grows.  
- Verify dependencies are properly isolated or injected.

---

## 🔐 6. Security & Safety
- Identify:  
  - Unsafe file handling (`open` without context manager).  
  - SQL injection risks if raw queries are used.  
  - Hardcoded credentials or API keys.  
  - Insecure use of `eval`, `exec`, `pickle`, etc.  
- Suggest using secure libraries (`secrets`, `hashlib`, etc.) where applicable.

---

## 🧪 7. Testing & Validation
- Check presence and coverage of unit tests.  
- Verify tests assert both expected and edge behavior.  
- Suggest adding mocking for I/O or external calls.  
- Ensure CI/CD or test automation hooks (if visible) are in place.

---

## 💬 8. Review Output Format
Respond with:  
- Summary of the overall code quality (1–2 sentences).  
- Key findings grouped under:  
  - ✅ Strengths  
  - ⚠️ Issues & Risks  
  - 💡 Suggestions for Improvement  

Include inline examples of corrected code where useful.  
Example:
```markdown
### ⚠️ Issues & Risks
- Function `process_data` modifies a list while iterating over it — can lead to skipped elements.
- Missing type hints for several functions.

### 💡 Suggestions
Use list comprehension for filtering:
```python
processed = [x for x in data if is_valid(x)]
```
```
