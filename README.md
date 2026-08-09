# Healthcare-Logistics-Supply-Chain-Performance-Analysis
**How my team and I transformed four years of healthcare logistics data into actionable insights—and what the experience taught me about Business Intelligence.


## Project Background

This project was developed during the **AI NOW Physical Bootcamp Hackathon** organized by **The Incubator Hub**.

The bootcamp brought together aspiring AI and data professionals to solve real-world business challenges through collaboration, analytics, and technology.

🔗 Learn more about The Incubator Hub:
[https://www.linkedin.com/company/the-incubator-hub/](https://www.linkedin.com/company/theincubatorng/)

🔗 AI NOW Program:
(https://www.youtube.com/live/PjOYGieFip0?si=Rg_kiK64bWCkVFUQ)


## Introduction

Healthcare logistics is more than moving medicines from suppliers to hospitals. It is about ensuring the right medicines are available at the right place, at the right time, and in the right quantity. Every delayed delivery, expired medicine, or stock shortage can disrupt hospital operations, increase costs, and ultimately affect patient care.

Behind every inventory transaction lies a business decision. Hospital administrators need to know which medicines require immediate replenishment, which suppliers consistently deliver on time, where inventory losses are occurring, and which facilities are most vulnerable to stock shortages. Without reliable data and actionable insights, making these decisions becomes difficult.

This case study presents a Healthcare Logistics & Supply Chain Performance Analysis solution developed during the AI NOW Physical Bootcamp Hackathon at The Incubator Hub. Working as part of a multidisciplinary team, we built an end-to-end Business Intelligence solution using Power BI. The project challenged us to transform four years of healthcare logistics data into meaningful insights that support inventory management, supplier performance monitoring, procurement planning, and pharmaceutical wastage reduction.

Rather than building dashboards for reporting alone, our objective was to create an interactive decision-support solution that enables healthcare stakeholders to monitor operations, identify supply chain risks, and make informed, data-driven decisions.

This document walks through the complete analytical journey—from understanding the business problem and preparing the data to designing the data model, developing DAX measures, building interactive dashboards, uncovering key insights, and providing actionable business recommendations.


## Business Problem

Healthcare supply chains play a critical role in ensuring that essential medicines are available when and where they are needed. However, public hospitals across Nigeria continue to face operational challenges such as medicine shortages, delayed supplier deliveries, and pharmaceutical wastage caused by expired stock. These issues disrupt patient care, increase operational costs, and reduce the overall efficiency of healthcare delivery.

One of the biggest challenges is that healthcare data is often fragmented. Inventory records, supplier information, procurement data, and medicine consumption records are stored across different systems, making it difficult for healthcare administrators to gain a complete view of supply chain performance. Without a centralized reporting solution, identifying stock shortages, monitoring supplier reliability, and planning procurement becomes a reactive process rather than a proactive one.

As a result, decision-makers struggle to answer critical business questions, such as:

- Which hospitals are most at risk of medicine shortages?
- Which medicines require immediate replenishment?
- Which suppliers consistently deliver late?
- How much inventory is lost due to expired medicines?
- Where should procurement teams prioritize their efforts?

To address these challenges, the objective of this project was to develop an interactive Power BI solution that consolidates healthcare logistics data into a single decision-support platform. The dashboard enables healthcare administrators to monitor inventory levels, evaluate supplier performance, reduce pharmaceutical wastage, and support evidence-based procurement decisions.



## Project Objectives

The primary objective of this project was to develop an interactive Business Intelligence solution that enables healthcare administrators to monitor supply chain performance and make data-driven decisions.

Specifically, the dashboard was designed to:

- Monitor medicine shortages across hospitals.
- Track supplier delivery performance.
- Identify medicines requiring immediate replenishment.
- Measure pharmaceutical wastage caused by expired stock.
- Improve inventory visibility.
- Support procurement planning through data-driven insights.



## Business Questions

Throughout the project, our analysis focused on answering the following questions:

- Which hospitals experience the highest medicine shortages?
- Which suppliers consistently deliver late?
- Which medicines expire most frequently?
- How much inventory is lost through wastage?
- Which products require immediate replenishment?
- Which hospitals should procurement teams prioritize?


## Dataset Overview & Understanding

The project uses four years of healthcare logistics data covering hospitals, medicines, suppliers, inventory transactions, and medicine deliveries. Together, these datasets represent the end-to-end healthcare supply chain—from medicine procurement and supplier deliveries to inventory management and hospital operations.

Before building the solution, our team explored how these datasets relate to one another and how each contributes to the healthcare supply chain. This understanding helped us identify the key business processes, define meaningful KPIs, and design dashboards that answer critical operational questions.

The datasets were then integrated into a relational star schema model in Power BI to support efficient reporting, reusable DAX calculations, and cross-functional analysis across procurement, inventory management, supplier performance, and pharmaceutical wastage.


## Data Cleaning

Before building the data model and dashboards, our team performed a series of data quality checks to ensure the dataset was accurate, consistent, and suitable for analysis. This process focused on improving data reliability across hospitals, medicines, suppliers, deliveries, and inventory records.

| **Cleaning Activity** | **Purpose** |
|------------------------|-------------|
| Validated row counts across all source tables | Ensured data completeness before analysis |
| Standardized State and LGA naming conventions | Removed inconsistencies caused by different text formats |
| Reviewed Hospital Type and Ownership values | Eliminated duplicate and inconsistent categories |
| Verified medicine names and strength information | Improved consistency in medicine records |
| Checked Unit Cost values | Identified invalid, blank, or negative values |
| Standardized supplier phone numbers | Ensured consistent contact information formatting |
| Validated supplier email addresses | Corrected malformed and inconsistent email records |
| Reviewed missing Contact Person values | Identified incomplete supplier records |
| Converted date fields to proper Date format | Enabled accurate time-based analysis and reporting |
| Validated inventory calculations | Verified **Opening Stock + Quantity Received − Quantity Dispensed − Quantity Expired** to identify discrepancies |
| Checked for negative inventory balances | Ensured stock quantities reflected realistic values |
| Validated delivery timelines | Flagged records where **Actual Delivery Date** occurred before the **Expected Delivery Date** |
| Documented all cleaning activities | Maintained a clear methodology for collaboration and presentation |

---

### Outcome

After the cleaning process, the dataset was consistent, reliable, and ready for data modeling, DAX calculations, and dashboard development. These validation steps improved the accuracy of inventory analysis, supplier performance evaluation, procurement monitoring, and pharmaceutical wastage reporting.


### Relational Star Schema Data Model
Relational star schema developed by our team to support healthcare supply chain analytics.

<img width="677" height="397" alt="image" src="https://github.com/user-attachments/assets/98bfe461-3b21-4262-a4c1-b9bb362726c9" />

The model connects transactional fact tables with descriptive dimension tables, enabling efficient filtering, improved report performance, and reusable DAX calculations. It also supports time intelligence, cross-functional analysis, and consistent reporting across inventory management, procurement, supplier performance, and pharmaceutical wastage.



## Data Model Summary

| **Table** | **Table Type** | **Purpose** | **Key Fields** |
|------------|----------------|-------------|----------------|
| **Inventory** | Fact Table | Stores medicine inventory movements, including opening stock, quantities received, dispensed, expired, and closing stock across hospitals. | InventoryID, HospitalID, MedicineID, QuantityReceived, QuantityDispensed, QuantityExpired, ClosingStock |
| **Deliveries** | Fact Table | Records medicine deliveries, enabling supplier performance analysis by comparing expected and actual delivery dates. | DeliveryID, SupplierID, HospitalID, DeliveryDate, ExpectedDeliveryDate, ActualDeliveryDate, QuantityDelivered |
| **Hospitals** | Dimension Table | Contains descriptive information about hospitals used for operational and capacity analysis. | HospitalID, HospitalName, HospitalType, State, BedCapacity, NumberOfDoctors, NumberOfPharmacists |
| **Medicines** | Dimension Table | Stores medicine attributes such as category, dosage form, storage requirements, and unit cost. | MedicineID, MedicineName, Category, DosageForm, StorageType, ShelfLifeMonths, UnitCost |
| **Suppliers** | Dimension Table | Contains supplier information used to evaluate delivery performance and procurement efficiency. | SupplierID, SupplierName, State, ContactPerson |
| **Date Table** | Dimension Table | Provides calendar attributes to support time intelligence, trend analysis, and year-over-year reporting. | Date, Day, Month, Quarter, Year |
| **Measures_DAX** | Measure Table | Contains reusable DAX measures used to calculate KPIs, business metrics, and analytical insights across the dashboards. | Average Delivery Delay, Supplier Delay %, Financial Wastage, Reorder Level, Stock Shortage Flag |


## DAX Measures & Business Logic

Our team developed reusable DAX measures to transform the healthcare logistics data into decision-ready KPIs across inventory, supplier performance, hospital operations, and pharmaceutical wastage.

### Basic KPIs

| **Measure** | **Purpose** |
|---|---|
| **Total Inventory Value** | Measures the monetary value of medicine inventory. |
| **Closing Stock** | Measures the quantity of medicine remaining in stock. |
| **Total Quantity Received** | Measures the quantity of medicines received. |
| **Total Quantity Dispensed** | Measures the quantity of medicines dispensed. |
| **Total Deliveries** | Measures the total number of deliveries recorded. |

### Analytical KPIs

| **Measure** | **Purpose** |
|---|---|
| **Supplier Delay %** | Measures the proportion of deliveries affected by delays. |
| **On-Time Delivery %** | Measures supplier delivery reliability. |
| **Average Delivery Delay (Days)** | Measures the average delivery delay. |
| **Expired Rate %** | Measures the proportion of medicine inventory that expired. |
| **% Hospitals Below Reorder Level** | Measures the proportion of hospitals operating below the required stock level. |

### Business Logic

| **Measure** | **Purpose** |
|---|---|
| **Stock Shortage Flag** | Identifies stock shortage conditions requiring attention. |
| **Low Stock Alert** | Highlights low-stock conditions. |
| **Expired Value (NGN)** | Quantifies the financial impact of pharmaceutical wastage. |
| **Reorder Level** | Supports identification of inventory requiring replenishment. |


## Dashboard Development

Our team translated the modeled healthcare logistics data and DAX measures into interactive Power BI dashboards designed to support different areas of healthcare supply chain management.

The solution consists of five key dashboard areas:

| **Dashboard** | **Focus** |
|---|---|
| **Executive Overview** | Provides a high-level view of inventory value, stock levels, medicine wastage, shortages, and overall supply chain performance. |
| **Hospital Profile** | Provides insights into hospital capacity, workforce, patient volume, and medicine availability. |
| **Supplier Performance** | Evaluates supplier delivery reliability, delays, early deliveries, and on-time performance. |
| **Inventory** | Monitors stock levels, reorder requirements, medicine categories, and inventory trends. |
| **Wastage Analysis** | Analyzes expired medicines, wastage costs, storage types, and supplier delivery performance. |


### Dashboard Design Approach

The dashboards were designed with a focus on clarity, usability, and decision-making. We used consistent navigation, KPI cards, interactive filters, trend analysis, and visual alerts to help users quickly identify supply chain risks and areas requiring attention.

The dashboards allow users to explore the data by factors such as **time, hospital, medicine, supplier, and location**, enabling more detailed analysis beyond the headline KPIs.



### Executive Overview

The Executive Overview provides a high-level view of the healthcare supply chain, bringing together inventory, wastage, stock availability, and operational indicators in one place.


<img width="1260" height="720" alt="image" src="https://github.com/user-attachments/assets/18eb826a-53b7-41d5-893f-559b2cf1abbf" />


A key finding is the **₦8.22bn total inventory value**, alongside **₦433m in expired medicine value** and a **4% expiry rate**, highlighting the scale of inventory being managed and the financial impact associated with medicine expiry.

The dashboard also highlights **73 low-stock alerts**, while **13 hospitals are currently below their medicine reorder level**, indicating areas where procurement and inventory teams may need to prioritize attention.

The inventory trend shows that quantities received generally remained above quantities dispensed across the period, with fluctuations over time. This provides visibility into inventory inflows relative to medicine utilization.



### Supplier Performance

The Supplier Performance dashboard evaluates delivery reliability across 2,000 recorded deliveries. **69% of deliveries were on time, while 31% experienced delays**, with an average delay of 2 days. Although 46% of deliveries arrived early, the delay rate highlights an opportunity to improve supplier reliability and delivery planning.

The supplier performance ranking enables procurement teams to compare suppliers, while the storage-type analysis shows that ambient products accounted for the largest quantity delivered at **1.8M units**.

<img width="1345" height="749" alt="image" src="https://github.com/user-attachments/assets/e7313432-c393-4be9-9bfa-846c21ecd705" />



### Hospital Profile

The Hospital Profile dashboard provides an overview of hospital capacity, workforce, patient volume, and medicine availability across **56 facilities**.

The hospitals collectively support approximately **13M annual patients** with a total capacity of **33K beds**. However, **94.4% of hospitals are below the medicine reorder level**, highlighting a significant inventory replenishment challenge despite the available clinical workforce and hospital capacity.

The workforce analysis provides additional context by showing the distribution of doctors and pharmacists across hospitals, helping decision-makers understand hospital capacity alongside medicine availability.

<img width="1303" height="735" alt="image" src="https://github.com/user-attachments/assets/4eb65ed0-8a3e-4aa0-8951-b15f19be996b" />

