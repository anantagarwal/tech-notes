# 📊 Data Warehousing Basics: Facts, Dimensions, and Schemas

## 🔹 Dimensions vs. Facts

### 📌 Facts

- Quantitative, measurable data.
- Stored in **fact tables**.
- Examples: `Sales Amount`, `Units Sold`, `Revenue`, `Profit`.

### 📌 Dimensions

- Descriptive attributes that provide **context** to facts.
- Stored in **dimension tables**.
- Examples: `Product Name`, `Date`, `Customer`, `Location`.

---

## 🧠 Example: Retail Sales

### 🧾 Fact Table – `Sales_Fact`

| Sale_ID | Date_Key | Product_Key | Store_Key | Units_Sold | Total_Amount |
|---------|----------|-------------|-----------|------------|--------------|
| 1       | 20250401 | 101         | 201       | 2          | 40.00        |

### 📅 Date Dimension – `Date_Dim`

| Date_Key | Date       | Day | Month | Year |
|----------|------------|-----|-------|------|
| 20250401 | 2025-04-01 | 01  | Apr   | 2025 |

### 🛍️ Product Dimension – `Product_Dim`

| Product_Key | Product_Name | Category | Brand |
|-------------|--------------|----------|-------|
| 101         | T-Shirt      | Clothing | Nike  |

### 🏬 Store Dimension – `Store_Dim`

| Store_Key | Store_Name | Location     |
|-----------|------------|--------------|
| 201       | Downtown   | New York, NY |

---

## ⭐ Star Schema

### 📌 Characteristics

- **Fact table** in the center
- Connected directly to **denormalized dimension tables**
- Simple and intuitive structure

### ✅ Pros

- Fast performance
- Easy to understand
- Great for BI tools (Power BI, Tableau, etc.)

### ❌ Cons

- Redundant data
- Larger storage

---

## ❄️ Snowflake Schema

### 📌 Characteristics

- Dimensions are **normalized** into sub-dimensions
- More structured and less redundant
- Requires more joins

### ✅ Pros

- Reduces data redundancy
- Better for complex hierarchies

### ❌ Cons

- Slower performance due to joins
- More complex structure

---

## ✅ When to Use

| Scenario                            | Best Schema   |
|-------------------------------------|---------------|
| Fast reporting                      | ⭐ Star Schema |
| Storage or complex hierarchy needed | ❄ Snowflake   |
| Simpler design                      | ⭐ Star Schema |
| Highly normalized data              | ❄ Snowflake   |

---

## 📚 Where It's Used

- Data Warehousing (Snowflake, Redshift, BigQuery)
- ETL/ELT Pipelines
- Business Intelligence (Power BI, Tableau, Looker)
- Sales & Financial Reporting


