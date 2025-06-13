# 🧪 Testing Report for E-Commerce Filter System

**Project:** E-Commerce Filter System  
**Date:** YYYY-MM-DD  
**Group Members:** @Member1, @Member2, @Member3

---

## 1. Expected Behaviors

1. Products should be filtered correctly based on the selected brand.
2. Products should appear or disappear based on the selected price range.
3. Only products with storage matching the selected value should be displayed.

---

## 2. Test Strategy

### Black-Box Testing Techniques

| Technique                | Scope                        | Example/Test Case Description                 |
|--------------------------|------------------------------|----------------------------------------------|
| Equivalence Partitioning | Brand, Price, Storage inputs | Test valid/invalid brands, price ranges      |
| Boundary Value Analysis  | Price, Storage               | Test 64GB, 1024GB, min/max price boundaries  |
| Decision Table Testing   | Filter combinations          | Test combinations of brand + price + storage |

### White-Box Testing Techniques

| Coverage Type   | Target Function(s)     | Tool/Method | Coverage (%) |
|-----------------|-----------------------|-------------|--------------|
| Statement       | applyFilters()        | Manual      | 100%         |
| Decision        | renderProducts()      | Manual      | 85%          |

---

## 3. Group Member Contributions

| Member    | Black-Box Techniques Applied          | White-Box Techniques Applied         | Other Contributions                |
|-----------|--------------------------------------|-------------------------------------|------------------------------------|
| @Member1  | Equivalence Partitioning: tested all brand and price ranges | Statement coverage: tested all lines in applyFilters() | Wrote bug report #12               |
| @Member2  | Boundary Value Analysis: tested min/max storage and price | Decision coverage: tested if/else in renderProducts() | Documented test cases, summary     |
| @Member3  | Decision Table: created filter combination matrix | Reviewed code paths and edge cases | Wrote bug report #14, reflections  |

*Each member should briefly describe their specific efforts and the techniques they applied.*

---

## 4. Defect Log & GitHub Issues

### Linked GitHub Issues

- [#12: Price filter does not display expected products](https://github.com/PLP-Database-DEPT/swt-w4/issues/12)
- [#14: Storage filter requires exact match](https://github.com/PLP-Database-DEPT/swt-w4/issues/14)

### Bug Report 1

**Title**: Price filter does not display expected products

**Steps to Reproduce**:
1. Select price range "1000-1500"
2. Click "Apply Filters"

**Expected**: Should display iPhone 14 Pro ($1499)  
**Actual**: No products displayed  
**Severity**: Medium

---

### Bug Report 2

**Title**: Storage filter requires exact match

**Steps to Reproduce**:
1. Select storage "256GB"
2. Click "Apply Filters"

**Expected**: Should display all products with 256GB storage  
**Actual**: Only displays products if storage is an exact string match  
**Severity**: Low

---

## 5. Reflection

**Challenges Faced:**  
- Ensuring all edge cases (e.g., minimum/maximum price) were tested.
- Interpreting ambiguous filter behaviors (e.g., overlapping ranges).

**Collaboration Benefits:**  
- Group discussions helped uncover bugs that were missed individually.
- Sharing test cases improved overall coverage and efficiency.

**Most Effective Techniques:**  
- Boundary value analysis quickly revealed issues at price/storage limits.
- Decision table testing was useful for complex filter combinations.

---

## 6. Coverage Gaps (Optional Visualization)


## 5. Coverage Gaps (Optional Visualization)
![mermaidjs](https://github.com/user-attachments/assets/3f0e2915-2256-42be-b3ba-40b0ce0413cc)

---

*End of Report*
