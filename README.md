# Franchise-Business-Intelligence-Dashboard-Template
# 📊 Franchise Business Intelligence Dashboard Template (Python + Plotly Dash)

A fully customizable, real-time dashboard framework for multi-branch businesses—perfect for cafes, retail chains, gyms, or service franchises. This template enables business owners and analysts to track key metrics like sales, inventory, customer behavior, and employee performance across multiple cities using Python and Dash.

---

## 📌 Project Overview

Franchises operating in multiple locations face challenges with data decentralization, inconsistent reporting, and real-time performance tracking. This project solves that by offering a dynamic dashboard system that aggregates operational data and presents it in an interactive, scalable, and user-friendly interface. The system simulates over 1000 rows of franchise-level data spanning 15 Indian and international cities and supports full drill-down analytics.

---

## 🛠️ Tech Stack

* **Python** – Core scripting and data processing
* **Pandas & NumPy** – Data management
* **Dash & Plotly** – Interactive UI and charts
* **Openpyxl / xlsxwriter** – Export to Excel
* **Power BI (optional)** – Comparative BI version

---

## 📁 Folder Structure

```
FranchiseBIDashboard/
├── data/
│   └── transactions.csv
├── app/
│   ├── app.py
│   ├── callbacks.py
│   ├── layout.py
│   └── utils.py
├── assets/
│   └── custom.css
├── reports/
│   └── ExportedReports/
├── docs/
│   ├── screenshots/
│   └── dashboard_flowchart.png
├── README.md
└── requirements.txt
```

---

## 🔍 Core Features

* 📈 **City/Branch-wise Sales Visualization**
* 🧾 **Inventory Status and Auto-alerts**
* 💼 **Employee Metrics: Service Time & Productivity**
* 📊 **Customer Behavior Charts (Footfall & Loyalty)**
* 📤 **Exportable reports (PDF/Excel)**
* 🌐 **Live filters: City, Product, Date, Branch Type**

---

## 🧠 Business Use Cases

* Benchmark branches using KPIs
* Discover high-performing teams/products
* Prevent stockouts with predictive restock alerts
* Optimize operations through location-level insights
* Monitor footfall to improve scheduling and promos

---

## 🔣 Sample Dashboard Code Snippet

```python
import pandas as pd
import plotly.express as px
import dash
from dash import dcc, html
from dash.dependencies import Input, Output

app = dash.Dash(__name__)
df = pd.read_csv('data/transactions.csv')

app.layout = html.Div([
    dcc.Dropdown(
        id='city-dropdown',
        options=[{'label': c, 'value': c} for c in df['City'].unique()],
        value='Mumbai'
    ),
    dcc.Graph(id='sales-bar')
])

@app.callback(
    Output('sales-bar', 'figure'),
    Input('city-dropdown', 'value')
)
def update_chart(city):
    filtered = df[df['City'] == city]
    fig = px.bar(filtered, x='Date', y='Sales', title=f"Sales in {city}")
    return fig

if __name__ == '__main__':
    app.run_server(debug=True)
```

---

## 📊 Simulated Data Columns

This dataset simulates real-world business operations for a multi-location franchise coffee chain. With over **30,000 rows of transactional data** spanning **15 global cities** and **3 branches per city**, it covers the full scope of operational KPIs needed for business intelligence analysis.

### 📘 Theoretical Overview

The dataset has been generated using Python and the Faker library to ensure statistical diversity while preserving realism. It includes customer traffic, employee performance, service metrics, sales, and product details—mimicking the actual daily activity of a nationwide brand.

This makes it suitable for analytics tasks such as:

* 📈 Sales analysis and growth tracking
* 📦 Inventory management & depletion alerting
* 🧑‍💼 Employee performance evaluation
* 🎯 Targeted customer segmentation (loyalty-driven)
* 🔁 Return trends and quality control

### 🔍 Fields and Business Mapping

| Column               | Description                                              |
| -------------------- | -------------------------------------------------------- |
| `Date`               | Date of transaction (past 6 months)                      |
| `City`               | One of 15 cities including Indian metros and global hubs |
| `Branch`             | Specific franchise branch (3 per city)                   |
| `Product`            | Type of beverage sold (Espresso, Mocha, etc.)            |
| `Sales`              | Revenue generated per transaction (₹150–₹550 range)      |
| `InventoryLevel (%)` | Remaining stock percentage at the time of transaction    |
| `CustomerFootfall`   | Number of walk-ins during the logged time block          |
| `EmployeeName`       | Staff member who fulfilled the order                     |
| `AvgServiceTime`     | Service time per transaction in minutes                  |
| `ReturnRate`         | Simulated % rate of dissatisfaction/returns (0–15%)      |
| `LoyaltySegment`     | Customer category: New / Returning / Loyal               |

This structured yet versatile dataset enables seamless exploration, business simulation, and advanced visualizations.

* `Date`, `City`, `Branch`, `Product`, `Sales`, `InventoryLevel (%)`, `CustomerFootfall`, `EmployeeName`, `AvgServiceTime`, `ReturnRate`, `LoyaltySegment`

---

## 🖼️ Screenshots

![Main Dashboard View](docs/screenshots/main_dashboard.png)
![Export Panel](docs/screenshots/export_section.png)
![Filter Interface](docs/screenshots/filter_ui.png)

---

## 🚀 Deployment

```bash
pip install dash pandas plotly openpyxl
python app/app.py
```

---

## 📈 Future Enhancements

* ☁️ Deploy to Streamlit Cloud or Render
* 🧠 Add predictive analytics using time-series models
* 🔐 Role-based access (Admin vs Branch Manager)
* 📲 Responsive mobile layout

---

## 👨‍💻 Author

**Pranjal Gurjar**
Franchise Data Intelligence | Dash Developer | MCA Final Year
📧 [gurjarpranjal.work@gmail.com](mailto:gurjarpranjal.work@gmail.com)
🔗 [GitHub Profile](https://github.com/pranjalgurjar)

---

## 📄 License

MIT License. Free to use for personal, academic, and commercial dashboard development with credit.
