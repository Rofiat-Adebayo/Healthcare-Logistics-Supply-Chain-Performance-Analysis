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


## Dataset Overview

The project uses four years of healthcare logistics data covering hospitals, medicines, suppliers, inventory transactions, and medicine deliveries. The datasets were integrated into a relational data model to support efficient reporting and cross-functional analysis across procurement, inventory management, supplier performance, and pharmaceutical wastage.

<img width="677" height="397" alt="image" src="https://github.com/user-attachments/assets/98bfe461-3b21-4262-a4c1-b9bb362726c9" />

### Figure 1. Power BI relational data model used to support analytics and reporting.

Working collaboratively, our team designed a relational data model in Power BI using a star schema approach. By connecting transactional fact tables with descriptive dimension tables, we created a model that supports efficient filtering, improves report performance, and provides a solid foundation for reusable DAX calculations and interactive dashboards.
Working collaboratively, our team designed a relational data model in Power BI using a star schema approach. By connecting transactional fact tables with descriptive dimension tables, we created a model that supports efficient filtering, improves report performance, and provides a solid foundation for reusable DAX calculations and interactive dashboards.

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



