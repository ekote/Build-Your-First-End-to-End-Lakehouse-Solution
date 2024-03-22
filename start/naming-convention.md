# Naming convention

> [!TIP]
> Please review the naming conventions as that is crucial for all the exercises to run smoothly. **No action needed, just review and ack the naming convention**.

## Workspace name
Assign a name: `urban-innovation-deNNN`, where NNN represents the number assigned to you. For example, `urban-innovation-de001` (Estera’s workspace).

## Bronze Layer (Raw Data Management)
Lakehouse Name: `bronzerawdata`

This is the foundational layer where raw data is ingested directly from various sources, including yellow and green taxi trip records, FHV trip records, and potentially other urban mobility datasets. The data is stored in its original, unmodified form. In the context of your workshop, this involves landing raw TLC Trip Record Data into this layer, ensuring that all raw data remains immutable and traceable for lineage purposes.

## Silver Layer (Refined Data Management)
Lakehouse Name: `silvercleansed`

In this intermediate layer, data is cleansed, standardized, and enriched to resolve inconsistencies and prepare for more detailed analysis. This includes resolving issues with data quality, standardizing formats, and enriching taxi and FHV data with additional contextual information, such as weather conditions or traffic data. The goal here is to create a reliable, query-optimized dataset that supports more efficient analysis and reporting.

## Gold Layer (Curated Data Management)
Lakehouse Name: `goldcurated`

The highest level of the lakehouse, where data is further transformed, modeled, and summarized to support advanced analytics and business intelligence. This layer focuses on deriving actionable insights and supporting high-level decision-making. It could involve aggregating data into meaningful metrics, developing KPIs for urban transportation efficiency, or building machine learning models to predict future trends based on historical patterns.
