# Noon Engineering Project

## Project Overview
This project focuses on developing an automated data pipeline to collect, process, and analyze mobile product data from the e-commerce platform **Noon**. The project involves web scraping, data transformation, and modeling to enable data-driven insights into the mobile market. Additionally, the entire pipeline is automated using cloud solutions, and data visualization is done using **Power BI**.

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
We aim to automate the collection, transformation, and analysis of mobile product data from Noon. By leveraging an efficient data pipeline, we aim to extract valuable insights into the mobile market with minimal manual intervention.

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

### Noon Scraping:
- Scraped mobile product data from Noon using Python's `BeautifulSoup` and `Requests` libraries.

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
- **Site Information**: Details about the site (Noon).
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
- Average mobile prices and trends from Noon.
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
- Python 3.10
- Azure Subscription (for Synapse Analytics, Data Lake)
- Power BI for visualization

### Steps

1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-repo/DEPI-project.git
   cd DEPI-project
---

## Folder Structure

```bash
e-commerce-data-engineering/
│
├── data/                        # Raw and processed data
├── scripts/                     # Python scripts for scraping and transformations
│   └── noon_scraper.py
│   └── transform_data.py
├── github/                      # GitHub Actions workflow files
│   └── .github/workflows/
├── power_bi_templates/           # Power BI dashboard templates
├── requirements.txt              # Python dependencies
├── README.md                     # Project documentation
└── LICENSE                       # License file
