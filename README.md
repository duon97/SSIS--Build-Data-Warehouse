## Case Study: Credit Card Usage Analysis

**Problem:**  
A bank wanted to analyze credit card usage, monitor card activity, and identify high-risk churn as well as potential customer segments for growth.

**Approach:**  

<img width="1241" height="616" alt="image" src="https://github.com/user-attachments/assets/0ac7695e-59ff-4a53-bf80-be5bb875884b" />

ETL Workflow
1. Load Data into Staging Layer

The ETL process begins by extracting data from the source system and loading it into a staging table.

Before each load, the staging table is refreshed to ensure a clean processing environment. The staging layer acts as a temporary workspace where raw data is prepared before entering the dimensional model.

Typical activities include:

Data cleansing
Data validation
Removing duplicates
Handling missing values
Standardizing formats and business values

The staging layer isolates source-system complexities from the warehouse structure.

2. Populate Dimension Tables

After the staging data has been cleansed, the ETL process loads dimension tables.

Each dimension is processed independently:

Gender
Attrition Flag
Education Level
Marital Status
Income Category
Card Category

During this step:

Distinct business values are identified.
New values are inserted into dimension tables.
Surrogate keys are generated for each dimension record.

This creates a standardized and reusable set of business entities within the warehouse.

3. Lookup Dimension Keys

Once all dimensions have been populated, the ETL process performs dimension lookups.

The original business values stored in the staging table are matched against their corresponding dimension records.

The generated surrogate keys are then assigned back to the staging table.

At this stage, the staging table contains:

Original business attributes
Corresponding dimension surrogate keys

This step establishes the relationships required by the Star Schema.

4. Load Fact Table

After all dimension keys have been resolved, the transformed staging data is loaded into the fact table.

The fact table stores:

Dimension foreign keys
Numerical measures
Transactional metrics
Analytical data used for reporting

Because dimension keys are already available, the fact table can be loaded while maintaining full referential integrity.
