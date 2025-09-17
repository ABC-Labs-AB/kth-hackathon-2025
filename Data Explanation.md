# 📊 Data Explanation

Before diving into the data, we strongly recommend reading the [**Case & Background**](<Case & Background.md>) document. This will provide important context that will help make sense of some of the variables and their relevance to the problem.

In brief, the dataset contains three different types of files: **Metadata**, **Key Transitions**, and **Individual Sample Files**.

## 📁 Dataset Structure in Your Bucket

All sample files are available in your assigned GCP bucket. The metadata has been split into training and test sets:

- **`metadata-train.csv`** - Contains 80% of the samples with labels (`interpreted_call`) for model training
- **`metadata-test.csv`** - Contains 20% of the samples **without labels** - this is your test dataset for final predictions
- **`key-transitions.csv`** - Complete analyte-transition mappings for all methods
- **Sample files** - Individual measurement files for all samples (both train and test)

**Important:** You must generate predictions for the test dataset (`metadata-test.csv`) as part of your final deliverables.

---

- [Metadata](#metadata) - labels and information on positive compounds found in each sample and a mapping to the sample file name.
- [Key Transitions](#key-transitions) - analyte-transition mappings for all compounds for all three methods.
- [Sample Files](#sample-files) - the detailed measurements for each sample.

Each of these file types will be explained separately in the following sections to help you understand their structure and role in modeling.

## Metadata

This file contains detailed information about each sample and its context.

| Variable Name | Description | Notes |
|--------------------|------------------------------------------------|-------------------------------------------------|
| `sample_file_name` | Mapping to the individual sample file | Data in GCP is in Parquet format; more details below |
| `test_type` | Type of run in a batch | Possible values: Analyte,Standard, QC, Blank |
| `positive_compounds`| List of all positive analytes detected in a sample | More details in [**Case & Background**](<Case & Background.md>). **Only present in training set**|
| `interpreted_call` | Positive/Negative label for the sample | "POS" means positive; "NEG" means negative. **Only present in training set** |
| `Method` | Indication of the testing method | Different methods test for different analytes; there are 3 methods used in our lab |
| `Instrument` | One of the 4 LC-MS/MS instruments used in the lab | |

#### 🔍 sample_file_name Breakdown

For example, take the sample file name:

20230314_U-DoA_001_JA_S_W3_111

| Part               | Example     | Meaning                                                                 |
|--------------------|------------|-------------------------------------------------------------------------|
| `20230314`         | 20230314   | Date in **YYYYMMDD** format → March 14, 2023                           |
| `U-DoA`            | U-DoA      | Method (e.g., *Urine – Drugs of Abuse*)                                |
| `001`              | 001        | Batch number of that day (→ Batch #1)                                  |
| `JA`               | JA         | Technician initials                                                    |
| `S`                | S          | Flag / condition (e.g., sample type, shift, or step indicator)         |
| `W3`               | W3         | Instrument ID (→ Workstation 3)                              |
| `111`              | 111        | Sample number within that batch                                        |

---

#### 🧾 Key Point
If you **remove the last number** (`111`), you're left with:

20230314_U-DoA_001_JA_S_W3

This represents the **batch name**.  
All samples in this batch will share this prefix, differing only by their final sample number.

## Key Transitions

This file describes the **analyte–transition mappings** for each *Processing Group* that each LC-MS/MS method is targeting.  
Quick reminder: each method is designed to detect different **specific compounds** based on a business need. Note also that when we talk about the results we use word Analyte/Compound to refer to a Processing Group e.g. Oxazepame is positive compound in a sample X.

| Variable Name | Description | Notes |
|--------------------|------------------------------------------------|-------------------------------------------------|
| `Processing_Group` | Target for LC-MS/MS detection | Equivalent to the positive_compounds field in [Metadata](#metadata) |
| `Analyte` | Compound used for identification of the Processing Group | |
| `Type` | Type of transition: Qualifier, Quantifier, or IS (Internal Standard) | For Qualifier and Quantifier, Analyte equals Processing Group; differs for IS |
| `Transitions` | Transition value | |
| `Predicted RT (mins)`| Predicted Retention Time (in minutes) | |
| `RT Window (mins)` | Allowed retention time window (in minutes) | |
| `Method` | Indication of the testing method | There are 3 different methods used in the lab, each testing for different analytes |

## 📂 Sample Files

Each file contains details measurements collected from the LC-MS/MS instrument.

| Variable Name | Description | Notes |
|---------------|-------------|-------|
| `time`        | Time point for this data point | |
| `Transition`  | The technical identifier for a specific analyte transition | In shorthand *Transitions* |
| `Intensity`   | Measured intensity (signal strength) | |
| `Data`        | Name of the sample this time point was collected for | By design corresponds to the sample filename prefix |
| `Method`      | Testing method used | There are **3 different methods** in the lab, each targeting different analytes |
| `Transitions` | Indicates which transition this data point belongs to | |