# Capture The Flag Challenge – STU160  
## FLAG1 and FLAG2 Extraction

This repository documents the process for identifying the manipulated book and generating **FLAG1** and **FLAG2** for the challenge.

Two datasets are provided:
- **books.csv**
- **reviews.csv**

A fake review was injected into the reviews dataset containing a unique personal hash derived from my student ID. Using this hash, I identify the fake review and the corresponding manipulated book.

---

## Step 1 — Compute Personal Hash (FLAG2)

The challenge requires computing:SHA256("STU034")

From this hash, I take the **first 8 hexadecimal characters**, convert them to **uppercase**, and this becomes: MY_HASH

I then search for this value inside the **reviews.text** column.

- Exactly **one review** contains this hash.
- That review is the **injected fake review**.
- FLAG2 is: {2CE049BE}


---

## Step 2 — Identify the Manipulated Book

The fake review contains a `parent_asin`, which links the review to a book in **books.csv**.

Steps:
1. Extract `parent_asin` from the matched review  
2. Find the corresponding book in **books.csv** using:books[books["parent_asin"] == target_parent_asin]


This gives the **single manipulated book** used for generating FLAG1.

---

## Step 3 — Compute FLAG1 From the Book Title

Once the manipulated book is identified:

1. Take its **title**
2. Remove all spaces
3. Take the **first 8 non-space characters**
4. Compute:SHA256(first8_characters)
The full SHA256 hex digest is **FLAG1**.







