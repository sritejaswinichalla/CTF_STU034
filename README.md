# Capture The Flag Challenge – STU034

## Workflow Summary

### 1. FLAG2 — Personal Hash
- Compute SHA256("STU034")  
- Take the first 8 hex characters (uppercase)  
- Search the text column in reviews dataset for this hash  
- The matching row identifies the fake injected review

### 2. FLAG1 — Book Title Hash
- Using the parent_asin of the fake review, locate the correct book  
- Remove spaces from its title  
- Take the first 8 characters  
- Compute SHA256 of that string → this is FLAG1
- parent_asin is the common attribute in both the datasets
