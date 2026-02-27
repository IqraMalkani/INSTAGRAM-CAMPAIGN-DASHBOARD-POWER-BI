# Rose Creme Instagram Campaign Performance Dashboard (Nov 2025-Feb 2026)

## 📌 Project Overview

Rose Creme is a Montreal-based dessert brand that acquires customers primarily through Instagram advertising.  
Users click ads → send DMs → complete orders via Interac transfer.

Because purchases are not tracked via Meta Pixel, **New Messaging Contacts** were used as the primary lead KPI.

This Power BI project evaluates:

- Campaign efficiency  
- Cost per messaging contact  
- Conversion quality  
- Budget allocation decisions (scale vs redesign)

---

## 🏗 Data Architecture

![Architecture](architecture.png)

### Model Design (Star Schema)

- **Fact Table:** `Campaign_Meta_Data`
- **Dimension Table:** `Campaign Mapping` (Campaign → Phase)
- **Dimension Table:** `DateTable` (Calendar + sorting structure)

### Relationships

- Campaign Mapping (1) → Campaign_Meta_Data (*)
- DateTable (1) → Campaign_Meta_Data (*)

This structure ensures clean filtering, correct aggregation, and scalable modeling.

---

## 📊 Dashboard – Executive Overview

![Executive Overview](screenshots/page1_executive_overview.png)

### KPIs

- Total Spend  
- Total New Messaging Contacts  
- Cost per New Messaging Contact  
- Messaging Conversion Rate  

Phase comparison:  
Winter → Product Expansion → Valentine Push  

This page provides leadership-level visibility into efficiency trends and volume shifts.

---

## 🔍 Campaign Diagnostic View

![Diagnostic View](screenshots/page2_diagnostic_view.png)

Includes:

- Performance Matrix (detailed breakdown)
- Cost Ranking (Bar Chart)
- Efficiency Quadrant (Scatter Plot: Spend vs Conversion Rate)
- Dynamic Phase Slicer
- Conditional formatting to flag zero-conversion campaigns

This view supports optimization and budget reallocation decisions.

---

## 🧮 Core DAX Measures

```DAX
Spend =
SUM('Campaign_Meta_Data'[Amount spent (CAD)])

Total New Messaging Contacts =
SUM('Campaign_Meta_Data'[New messaging contacts])

Cost per New Msg Contact =
DIVIDE([Spend], [Total New Messaging Contacts])

Messaging Conversion Rate =
DIVIDE(
    [Total New Messaging Contacts],
    SUM('Campaign_Meta_Data'[Unique clicks (all)])
)

```
---

## 📈 Key Insights

- **Product Expansion** generated the highest messaging volume.
- **Winter Campaign** delivered the lowest cost per acquisition.
- **Valentine phase** showed rising CPA with moderate conversion strength.
- One campaign generated spend without conversions (flagged via conditional formatting).
- High-conversion, low-spend campaigns identified as strong scale candidates.

---

## 🎯 What This Project Demonstrates

- Business KPI translation into measurable analytics
- Power Query data cleaning & transformation
- Professional star schema modeling (Fact + Dimensions)
- Advanced DAX measure construction
- Marketing performance optimization analysis
- Executive dashboard storytelling

---

## ⚠ Limitations

- No tracked revenue (payments via Interac)
- Aggregated export (no daily time breakdown)
- No CRM integration for true ROI calculation

---

## 🚀 Future Improvements

- Integrate order-level data
- Build full funnel analysis (Impressions → Clicks → Messages → Orders → Revenue)
- Add time-intelligence (Month-over-Month growth)
- Automate refresh using structured folder source


## Dashboard

You can view the sales analysis dashboard here:  
https://app.powerbi.com/view?r=eyJrIjoiYThjYmZjNjUtZjM4Ni00MDExLTgyMzMtOWMwNjhmODA5OWIyIiwidCI6ImYwZTZkMmNhLTg3MjgtNDgxMy1hYTI4LTM2MmM4NmNmMjBlNSJ9&pageName=78c0740403ed0ab68957

## 🛡️ License

This project is licensed under the [MIT License](LICENSE). You are free to use, modify, and share this project with proper attribution.

## 🌟 About Me

Hi, I’m Iqra Malkani. I’m passionate about working with data and building projects across SQL, Power BI and Excel. I focus on creating practical solutions that turn data into meaningful insights and showcase skills that are valuable for business and analytics roles.

You can explore more of my work on my website: www.iqramalkani.com


