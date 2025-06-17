# 🧪 Testing Report for E-Commerce Filter System

**Project:** E-Commerce Filter System  
**Date:** 2025-06-16
**Group Members:** [Rose Kabingu](), [Jeptum Brenda](https://github.com/bjeptum), [Apeh Adams](https://github.com/adamsap1)

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

---

### Equivalence Partitioning Report
1. Objective:
   - Verify that the filters works correctly handling both valid and invalid selections by Brand, Price Range and Storage
   
2. Test Item
  - Filter system: Brand dropdown, Price Range dropdown, Storage input field.

3. Partitions
   
| Filter Type   | Input    |
|-----------------|----------------------- |
| Brand | Apple (P1A), Samsung (P1B), Google (P1C), all (P1D) |
| Price($)    | 0-500(P2A), 500-1000(P2B), 1000-1500(P2C), all(P2D) |
| Storage(GB) | 64(P3A), 512(P3B), 1024(P3C), empty(P3D), below range(P3E), above range(P3F)| non-numeric(P3G) |

4. Test Cases


| ID   | Brand     | Price Range($) | Storage(GB) | Partition(s)  | Expected Result                                                  | Actual Result |
| ---- | --------- | ----------- | ------- | ------------- | ---------------------------------------------------------------- | -------------- |
| TC01 | All Brands| Any Price| empty | P1D, P2D, P3D | Shows all 6 products                                          | Shows all 6 products|
| TC02 | apple   | Any Price| empty | P1A, P2D, P3D | Show all Apple products (3 items)    | Shows all Apple products|
| TC03 | All Brands | 0–500 | empty | P1D, P2A, P3D | Show products priced ≤ 500(1 item)               | Shows 1 item iphone SE |
| TC04 | All Brands | Any Price | 512     | P1D, P2D, P3B | Show storage = 512 (1 item)                | Shows 1 item Galaxy S22|
| TC05 | samsung | 500–1000  | empty| P1B, P2B, P3D | Should show Galaxy S22 (price 999)                    | Shows  Galaxy S22 (price 999) |
| TC06 | All Brands | 1000–1500 | empty | P1D, P2C, P3D | Show prices 1000–1500 (2 items)                     | Shows 2 items Iphone 14 Pro, Galaxy Z Flip|
| TC07 | All Brands | Any Price | 63      | P3E (invalid) | Show storage error message; no filtering                | Show error message; filtering is not updated |
| TC08 | All Brand | Any Price | 1025    | P3F (invalid) | Storage invalid; error message                        | Shows error message; filtering is not updated |
| TC09 | All Brands | Any Price| abc     | P3G (invalid) | Same invalid format handling                           | Does not accept non-numeric entry; filters to show all 6 products |
| TC10 | google  | 0–500     | 128     | P1C, P2A, P3B | Error message              |  Shows error message|
| TC11 | apple   | 1000–1500 | 1024    | P1A, P2C, P3C | iPhone 14 Pro (1 item) | Shows 1 item iPhone 14 Pro |
| TC12 | samsung | 1000–1500 | 512     | P1B, P2C, P3B | Show Galaxy Z Flip (1 item)             | Shows 1 item;  Galaxy Z Flip |
| TC13 | apple   | 0–500    | empty    | P1A, P2A      | Show only iPhone SE (1 item)   | Shows 1 item iPhone SE |

---
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

- [#12:Storage Filter Fails for 512GB and 1024GB](https://github.com/PLP-Database-Design/week-4-rosewanjirukabingu/issues/2)
- [#14: Storage filter requires exact match](https://github.com/PLP-Database-DEPT/swt-w4/issues/14)

### Bug Report 1

title: Storage Filter Fails for 512GB and 1024GB

The storage filter does not display any products when set to 512GB or 1024GB, even though products with these capacities exist in the database.

Steps to Reproduce:

select the brand you want.
Set the storage filter to "512GB" or "1024GB".
Click "Apply Filters"
Expected: Products with storage capacities of 512GB and 1024GB should be displayed depending on which brand is selected.
Actual: no product is displayed.
Severity: High

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
