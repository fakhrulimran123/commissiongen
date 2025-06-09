# commissiongen

# 🧮 Commission Calculation Web App

This project is a custom-built internal tool designed to **automate monthly commission calculations** based on tiered pricing logic for a distribution company.

It connects to an MSSQL database (Microsoft Dynamics AX), extracts relevant payment data, applies business-specific commission rules, and generates a clean, structured report for finance or sales teams.

> 💡 **Note:** The hosted version on AWS EC2 is currently **offline** to avoid hosting charges. You can still run the app locally using the instructions below.

---

## 🚀 Features

- Extracts and transforms payment data from MSSQL (`Z_ONLYDONEPAYMENT` table)
- Applies complex, tier-based commission logic
- Generates exportable reports
- Optional web interface built with Vue.js
- Fully automatable using Power Automate + SharePoint
- Clean and responsive UI with Tailwind CSS

---

## 🛠️ Tech Stack

### Backend
- **Python 3**
- **Pandas** – for data manipulation
- **SQLAlchemy / pyodbc** – for MSSQL database connection

### Frontend (Optional)
- **Vue.js**
- **Tailwind CSS**

### Automation & Integration
- **Power Query (Excel)** – Commission logic can also be replicated in Excel
- **Power Automate** – Automates monthly report generation and upload to SharePoint

### Deployment Tools (Optional)
- **AWS EC2 (Ubuntu)** – Web server (offline)
- **Gunicorn + Nginx** – For production deployment

---

## 📊 Commission Logic

Commission is calculated based on where the **Selling Price** falls within defined pricing tiers:

| Price Range                               | Commission Rate |
|-------------------------------------------|------------------|
| Min Price < Selling Price < DSM Price     | 1.0%             |
| DSM Price < Selling Price < DSR Price     | 2.0%             |
| DSR Price < Selling Price < Tier 1 Price  | 2.5%             |
| Tier 1 Price < Selling Price < Tier 2 Price| 3.0%            |
| Tier 2 Price < Selling Price < Tier 3 Price| 4.0%            |
| Selling Price > Tier 3 Price              | 5.0%             |

---

## 🖥️ Local Setup

### Prerequisites

- Python 3.x
- MSSQL Database Access
- Node.js & npm (if using the frontend)
- Excel/Power Query (optional)
- Git

### 1. Clone the Repository

```bash
git clone https://github.com/fakhrulimran123/commission-web-app.git
cd commission-web-app
