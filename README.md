# 🧪 Week 4 Assignment: Test Design Techniques 

## 🎯 **Learning Objectives**
* Apply **black-box** (equivalence partitioning, boundary analysis, decision tables) and **white-box** (statement, decision coverage) testing techniques.
* Collaborate in groups of 3 to identify and document bugs via GitHub Issues.
* Summarize findings in a structured `Test_Report_Summary.md`.

---

## 📋 **What You'll Need**
* 💻 A browser (e.g., Chrome, Firefox, or Edge).
* 📂 The provided [e-commerce filter system](index.html).
* 🌐 Access to the course GitHub repository.

---

## 🛠️ **Group Collaboration**
- Form groups of **3**. Each group will work together to complete the assignment and submit a single report.

---

## 📝 **Submission Instructions**  
1. **Create a single `Test_Report_Summary.md` file** that includes:
   - ✅ A list of **3 expected behaviors** of the e-commerce filter system.
   - 🔗 Links to **2 GitHub Issues** raised by the group, following the format below.
   - **Summary of black-box and white-box testing techniques applied** during the assignment.

2. **Raise the bug reports directly on GitHub** using the Issues tab of the class repository. These issues will be referenced by ID and linked in your `Test_Report_Summary.md` file.

### Bug Report Format
```markdown
**Title**: [e.g., "Price filter does not display expected products"]

**Steps to Reproduce**:
1. Select price range "1000-1500"
2. Click "Apply Filters"

**Expected**: Should display iPhone 14 Pro ($1499)  
**Actual**: No products displayed  
**Severity**: Medium
```

---

## 🚀 **Run in VS Code (Live Server)**

### **Prerequisites**
- Install [VS Code](https://code.visualstudio.com/download)
- Add the [Live Server extension](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

### **Quick Setup**
1. Clone and open the repository:
   ```bash
   git clone https://github.com/PLP-Database-DEPT/swt-w4.git
   cd swt-w4
   code .
   ```

2. Open `index.html` in VS Code's Explorer (Ctrl+Shift+E), right-click, and select Open with Live Server.

---

## 📚 **Assignment Questions**

### Question 1 📋  
Write down **3 expected behaviors** that the e-commerce filter system should have in the `Test_Report_Summary.md` file.  
📌 Example:
* Products should be filtered correctly based on selected brand.

### Question 2 🐛  
Test the e-commerce filter system by interacting with the application.  
Find and report **2 bugs** using GitHub Issues. Use the provided format above.

---

## 🧪 **Testing Techniques to Apply**

### Black-Box Testing
- **Equivalence Partitioning**: Identify valid and invalid input classes for filters (e.g., brands, price ranges).
- **Boundary Value Analysis**: Test edge values for storage input (e.g., 64GB, 1024GB).
- **Decision Table Testing**: Create a decision table for filter combinations and expected outputs.

### White-Box Testing
- **Statement Coverage**: Ensure all executable statements in the code are tested.
- **Decision Coverage**: Test all decision points in the filtering logic (e.g., if/else conditions).

---

## 💭 **Reflection**  
Capture your group's reflections in the `Test_Report_Summary.md` file. Discuss:
- What challenges did you face during testing?
- How did collaboration help in identifying bugs?
- What black-box and white-box techniques were most effective?

*How to edit a [markdown file](https://www.markdownguide.org/basic-syntax/#headings)*

### NOTE: You should not fork the repository.
