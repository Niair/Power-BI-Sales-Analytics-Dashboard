# Power BI Sales Analytics Dashboard

## 📊 Dashboard Documentation

### Download Full Report
[![Download Dashboard PDF](https://img.shields.io/badge/Download_Full_Report-EC1C24?style=for-the-badge&logo=adobe-acrobat-reader&logoColor=white)](powerbi/Superstore_Sales.pdf)

## 📌 Overview
A professional sales analytics dashboard built with Power BI that provides insights into:
- Revenue trends
- Profitability analysis
- Geographic performance
- Product/category performance
- Customer segmentation

## 🛠️ Technical Stack
- **Data Source**: Superstore sales data (CSV/Excel)
- **Tools**:
  - Power BI Desktop
  - Power Query (ETL)
  - DAX (Measures & Calculated Columns)
- **Key Features**:
  - Time intelligence filtering
  - Drill-through capabilities
  - Mobile-responsive design

## 📂 File Structure
```
/superstore-analytics/
│
├── /data/                    # Raw data files
│   └── superstore.csv        # Source dataset
│
├── /powerbi/                 # Power BI files
│   └── superstore-dashboard.pbix  # Main dashboard file
│
└── README.md                 # This documentation
```

## 🔧 Setup Instructions

### 1. Data Preparation
```dax
// Date table creation
Date = 
CALENDAR(
    MIN(superstore[Order Date]),
    MAX(superstore[Ship Date])
)
```

### 2. Key DAX Measures
```dax
// YTD Sales
Sales YTD = 
TOTALYTD(
    SUM(superstore[Sales]),
    'Date'[Date]
)

// YoY Growth
Sales Growth YoY = 
VAR CurrentYear = [Total Sales]
VAR PriorYear = CALCULATE([Total Sales], DATEADD('Date'[Date], -1, YEAR))
RETURN DIVIDE((CurrentYear - PriorYear), PriorYear)
```

### 3. Dashboard Features
| Component | Purpose | Key Fields |
|-----------|---------|------------|
| Year Slicer | Time filtering | `Date[Year]` |
| Sales Trend | Monthly performance | `Order Date`, `Sales` |
| Profit Map | Geographic analysis | `State`, `Profit` |
| Product Matrix | Top performers | `Product Name`, `Sales`, `Profit Margin` |
