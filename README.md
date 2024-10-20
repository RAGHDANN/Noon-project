# E-Commerce Data Engineering Project

## Project Overview
This project focuses on developing an automated data pipeline to collect, process, and analyze mobile product data from two major e-commerce platforms: **Amazon** and **Noon**. The project involves web scraping, data transformation, and modeling to enable data-driven insights into the mobile market. Additionally, the entire pipeline is automated using cloud solutions, and data visualization is done using **Power BI**.

---

## Table of Contents
- [Project Objective](#project-objective)
- [Tech Stack](#tech-stack)
- [Data Collection](#data-collection)
- [Data Transformation](#data-transformation)
- [Data Modeling](#data-modeling)
- [Pipeline Automation](#pipeline-automation)
- [Visualization](#visualization)
- [Future Enhancements](#future-enhancements)
- [How to Run the Project](#how-to-run-the-project)
- [Contributors](#contributors)
- [License](#license)

---

## Project Objective
Our goal is to automate the collection, transformation, and analysis of e-commerce data from Amazon and Noon for mobile products. By leveraging an efficient data pipeline, we aim to extract valuable insights into the mobile market with minimal manual intervention.

---

## Tech Stack
- **Programming Language**: Python
- **Libraries**: BeautifulSoup, Requests, Pandas, Asyncio, I/O
- **Automation & Cloud**:
  - Azure Synapse Analytics
  - Azure Data Lake (serverless)
  - GitHub Actions
  - Azure Functions
- **Visualization**: Power BI

---

## Data Collection

### Amazon and Noon Scraping:
- Scraped mobile product data using Python's `BeautifulSoup` and `Requests` libraries.
- Solved CAPTCHA using OCR techniques during Amazon scraping.

### Data Collected Includes:
- Product specifications (model, brand, OS, RAM, etc.)
- Pricing details (price, discount, currency)
- Reviews and ratings

---

## Data Transformation
- Cleaned and transformed raw data using `Pandas`.
- Handled missing values, removed duplicates, and ensured data consistency.
- Converted currency values to USD and calculated additional metrics such as discount percentages and prices without discounts.

---

## Data Modeling

### Designed Star Schema for Data Warehouse:
- **Fact Table**: Contains product ID, price, rating, and review information.
- **Dimension Tables**: Specifications, site details, reviews, and date.

### Fact Table Columns:
- `product_id` (FK), `site_id` (FK), `price_usd`, `discount`, `rating_avg`, `review_count`

### Dimension Tables Include:
- **Device Specifications**: Product details like model name, OS, RAM, storage, etc.
- **Site Information**: Details about the site (Amazon, Noon).
- **Review Details**: User reviews and ratings.
- **Date Table**: Date-related fields (day, month, year).

---

## Pipeline Automation
- Initially used **Azure Synapse Analytics** and **Spark pool notebooks** for automation.
- Transitioned to using **Azure Functions** with **GitHub Actions** for triggering the entire pipeline.

### The Automated Pipeline Performs:
1. Scraping data at scheduled intervals.
2. Data cleaning and transformation.
3. Loading data into a serverless **Azure Data Lake**.
4. Creating external tables in **Azure Synapse** for data warehousing.

---

## Visualization
- Pulled data into **Power BI** for creating interactive dashboards.

### Key Insights Include:
- Average mobile prices and trends across Amazon and Noon.
- Product ratings and review counts.
- Comparative analysis of mobile product specifications.

---

## Future Enhancements
- Integrate additional data sources for a more comprehensive view of the mobile market.
- Implement advanced analytics techniques for predictive modeling and market trend analysis.
- Further optimize the automation process to reduce costs and improve efficiency.

---

## How to Run the Project

### Prerequisites
- Python 3.8+
- Azure Subscription (for Synapse Analytics, Data Lake, Functions)
- Power BI for visualization

### Steps

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-repo/DEPI-project.git
   cd DEPI-project

2. **Set Up Azure Functions**:
   - Deploy the Azure Functions using the provided deployment scripts to automate the scraping and data processing tasks.
   - Schedule the functions to run at defined intervals using Azure's built-in scheduler or timers.

3. **Set Up GitHub Actions**:
   - Configure GitHub Actions to trigger the pipeline automation process.
   - Use the `.github/workflows/` directory in the repository to set up actions for continuous integration and deployment (CI/CD) for the pipeline.
   - Actions can automate tasks like:
     - Scraping and processing data
     - Deploying updated functions to Azure
     - Monitoring pipeline health and issues

4. **Connect Power BI**:
   - Once data is loaded into the Azure Data Lake and transformed into external tables via Azure Synapse, connect Power BI.
   - To connect Power BI:
     1. Open Power BI Desktop.
     2. Select "Get Data" and choose "Azure Data Lake Storage" or "Azure Synapse Analytics".
     3. Connect to your data lake or data warehouse and load the required tables.
     4. Use the provided Power BI template (found in the `/power_bi_templates/` folder) to create the visualizations and dashboards.

5. **Customize Power BI Dashboards**:
   - Use the Power BI dashboards to visualize key insights.
   - Customize the visualizations further by applying filters, slicers, and charts as needed to analyze the mobile product data across different dimensions (price, ratings, reviews, etc.).

---

## Troubleshooting

### Common Issues:
- **CAPTCHA Errors during Scraping**: 
  - Ensure OCR libraries are correctly installed and working to bypass CAPTCHA challenges.
  - If scraping fails, increase the delay between requests to avoid detection.
  
- **Azure Synapse Connection Issues**:
  - Verify that your Azure credentials and permissions are correctly configured.
  - Ensure that external tables in Azure Synapse are correctly mapped to the data lake.

- **Power BI Data Loading Errors**:
  - Make sure your Power BI account has access to Azure resources.
  - Ensure the data source connection strings and credentials are correctly set up.

---

## Folder Structure

```bash
e-commerce-data-engineering/
│
├── data/                        # Raw and processed data
├── scripts/                     # Python scripts for scraping and transformations
│   └──  noon_ETL.ipynb
├── github/                      # GitHub Actions workflow files
│   └── .github/workflows/
├── power_bi_templates/           # Power BI dashboard templates
├── requirements.txt              # Python dependencies
├── README.md                     # Project documentation
└── LICENSE                       # License file

