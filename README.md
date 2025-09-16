# 📊 Layoffs SQL Data Cleaning Project

This project focuses on cleaning, standardizing, and preparing a dataset containing layoff data from tech companies for further analysis. All transformations were performed using **SQL**.

---

## 🗂️ Database Information

- **Database**: `world_layoffs`
- **Original table**: `layoffs`
- **Staging tables**: `layoffs_staging` and `layoffs_staging2`

The dataset includes the following information:
- Company name
- Location
- Industry
- Total laid off
- Percentage laid off
- Date
- Company stage
- Country
- Funds raised (in millions)

---

## ⚙️ Project Steps

### 1. 🔁 Removing Duplicates

- Copied the original `layoffs` table into `layoffs_staging`
- Used `ROW_NUMBER() OVER(PARTITION BY ...)` to identify duplicate records
- Deleted duplicate rows in a new staging table `layoffs_staging2` to preserve the cleaned data

### 2. 🧹 Data Standardization

- Removed extra spaces from company names using `TRIM()`
- Standardized industry names (e.g., replacing `"Crypto / Blockchain"` with `"Crypto"`)
- Cleaned country names by removing unwanted punctuation (e.g., `"United States."` → `"United States"`)
- Converted the `date` column from `TEXT` to `DATE` using `STR_TO_DATE()`

### 3. 🚫 Handling Null or Blank Values

- Identified records with missing `industry`, `total_laid_off`, or `percentage_laid_off`
- Replaced blank industries by cross-referencing records from the same company
- Removed rows where both `total_laid_off` and `percentage_laid_off` were null

### 4. 🧯 Removing Unnecessary Columns

- Dropped the `row_num` column after using it for duplicate detection

---

## 📌 Final Outcome

The final cleaned table `layoffs_staging2` includes:
- No duplicate records
- Properly formatted date values
- Standardized and consistent data entries
- Only relevant and complete records

## 📁 Project Structure

