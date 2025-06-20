# 🧪 Testing Report for E-Commerce Filter System

**Project:** E-Commerce Filter System  
**Date:** 2025-06-15

**Group Members:** [Rose Kabingu](https://github.com/rosewanjirukabingu), [Jeptum Brenda](https://github.com/bjeptum), [Apeh Adams](https://github.com/adamsap1)

---

## 1. Expected Behaviors

1. Brand Filter

Products should be filtered correctly based on the selected brand.

2. Price Range

Products should appear or disappear based on the selected price range.

3. Storage Filter

Only products with storage matching the selected value should be displayed.

4. Combined Filters

When multiple filters are applied(e.g., brand = price + storage), only  products that match all selected criteria should be displayed.

5. Reset/Clear Behavior

Clearing or resetting filters should return the full, unfiltered product list.

---

## 2. Test Strategy

### Black-Box Testing Techniques

| Technique                | Scope                        | Example/Test Case Description                 |
|--------------------------|------------------------------|----------------------------------------------|
| Equivalence Partitioning | Brand, Price, Storage inputs | Test valid/invalid brands, price ranges      |
| Boundary Value Analysis  | Price, Storage               | Test 64GB, 1024GB, min/max price boundaries  |
| Decision Table Testing   | Filter combinations          | Test combinations of brand + price + storage |


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
### Boundary Value Analysis Report

1. Price Filter Boundaries

  - Valid Range: $ 0 - $1500

| Test Value         | Source         | Expected Behavior                      | Actual Result | 
|--------------------|----------------|----------------------------------------------------------------|------|
| 499                | Below 0–500 boundary | Rejected and no products shown | No products shown |
| 500                | Lower boundary of 500–1000 | Return matching products | Galaxy S22|
| 501                | Above 500  | Return products in 500–1000 range           | Galaxy S22     |
| 999                | Below upper | Return products less than or equal to 999   | Galaxy S22                           |
| 1000               | Exact boundary of 1000–1500 | Return products including price = 1000|No products shown |
| 1001               | Above 1000 | Return matching products |Galaxy Z Flip, iPhone 14 Pro |
| 1499               | Below max | Return items less than 1500    | Galaxy Z Flip, iPhone 14 Pro|
| 1500               | Upper boundary | Return items priced at 1500  | Galaxy Z Flip, iPhone 14 Pro|
| 1501               | Above max | Rejected  and display no result| No products shown |



2. Storage Filter Boundaries
 
 - Valid Range: between minimum 64GB  and maximum 1024GB.

| Test Case | Input | Expected | Result |
|-----------|-------|----------|--------|
| TC1       | 64    | Accepted | Return exact matching products; only 64GB products |
| TC2       | 63    | Rejected | Trigger Validation error: error message shown: Must be between 64–1024 GB|
| TC3       | 65    | Accepted | Return exact matching products; none in this case|
| TC4       | 1024  | Accepted | Return exact matching products; only 1024GB products |
| TC5       | 1025  | Rejected | Trigger Validation error: error message shown: Must be between 64–1024 GB |
| TC6       | 1023  | Accepted | Return exact matching products; none in this case|
| TC7       | empty | Accepted | Return exact matching products; all products in this case |
| TC8       | abc   | Rejected | Does not accept inputting non-numeric value |




### White-Box Testing Techniques

| Coverage Type   | Target Function(s)     | Tool/Method | Coverage (%) |
|-----------------|-----------------------|-------------|--------------|
| Statement       | applyFilters()        | Jest (unit test) | 100%         |
| Decision        | renderProducts()      | Jest (unit test) | 85%          |

#### Test Execution Summary

- Test Suites: 1 passed, 1 total
- Tests: 7 passed, 7 
- totalTime: ~0.6s

### Test Case Summary

**`applyFilters()` – Filter Logic**

| TC  | Description                           | Covered Logic               |
|-----|---------------------------------------|-----------------------------|
| TC1 | No filters applied                    | All if blocks skipped     |
| TC2 | All filters valid                     | All if branches taken     |
| TC3 | Storage below min (e.g. 32GB)         | Validation error triggered  |
| TC4 | Only brand selected                   | Only brand condition true   |
| TC5 | Storage too high (e.g. 2048GB)        | Validation error triggered  |

**`renderProducts()` – Rendering Logic**

| TC  | Description             | Expected Behavior          |
|-----|-------------------------|----------------------------|
| TC6 | Products available      | Cards rendered             |
| TC7 | No products to display  | No results shown   |

**Note:** All white box test cases passed
---

## 3. Group Member Contributions

| Member    | Black-Box Techniques Applied          | White-Box Techniques Applied         | Other Contributions                |
|-----------|--------------------------------------|-------------------------------------|------------------------------------|
| [Jeptum Brenda](https://github.com/bjeptum)  | Equivalence Partitioning: tested all brand and price ranges; Boundary Value Analysis: tested min/max storage and price; Decision Table: created filter combination matrix   |Statement coverage: tested all lines in applyFilters()  | Wrote bug report [1]()       
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
