# Dataset Description

## Overview

This dataset contains sales, inventory, and product data for 123 products over a 3-year period (2023–2025). It is designed for demand forecasting, inventory optimization, and supply chain analytics tasks.

---

## Files

### 1. `sales_train_2023_2024.csv`

Historical monthly sales and inventory levels for all products covering **January 2023 – December 2024** (24 months). This is the training set.

| Column | Description |
|--------|-------------|
| `ProductID` | Unique product identifier (e.g., P001, P002, ..., P123) |
| `Product_name` | Human-readable product name |
| `Type` | Row type: `Sales` (units sold) or `Inventory_level` (end-of-month stock in units) |
| `2023-01` ... `2024-12` | Monthly values — either units sold or inventory level depending on the `Type` column |

Each product has exactly **2 rows**: one for Sales and one for Inventory_level.

---

### 2. `sales_test_2025.csv`

Monthly sales and inventory levels for all products covering **January 2025 – December 2025** (12 months). This is the test set / target period for forecasting.

| Column | Description |
|--------|-------------|
| `ProductID` | Unique product identifier |
| `Product_name` | Human-readable product name |
| `Type` | Row type: `Sales` (units sold) or `Inventory_level` (end-of-month stock in units) |
| `2025-01` ... `2025-12` | Monthly values for the forecast horizon year |

Same structure as the training file — 2 rows per product.

---

### 3. `products_parameters.csv`

Static product-level attributes relevant to inventory management and cost optimization.

| Column | Description |
|--------|-------------|
| `ProductID` | Unique product identifier |
| `Product_name` | Human-readable product name |
| `Storage_cost_PLN_per_unit_month` | Monthly warehousing/holding cost per unit (in PLN) |
| `Shelf_life_months` | Product shelf life in months |
| `Lead_time_months` | Supplier lead time in months (time from order to delivery) |
| `Safety_stock_months` | Recommended safety stock expressed in months of average demand |
| `Price_PLN_per_unit` | Unit selling price (in PLN) |

One row per product (123 rows total).

---

### 4. `financial_plan.csv`

Annual sales plan / budget targets for each product across 2023, 2024, and 2025.

| Column | Description |
|--------|-------------|
| `ProductID` | Unique product identifier |
| `Product_name` | Human-readable product name |
| `Plan_2023_units` | Planned annual sales volume for 2023 (units) |
| `Plan_2024_units` | Planned annual sales volume for 2024 (units) |
| `Plan_2025_units` | Planned annual sales volume for 2025 (units) |
| `Plan_2023_PLN` | Planned annual sales revenue for 2023 (PLN) |
| `Plan_2024_PLN` | Planned annual sales revenue for 2024 (PLN) |
| `Plan_2025_PLN` | Planned annual sales revenue for 2025 (PLN) |
| `Price_PLN_per_unit` | Unit selling price used for plan calculations (PLN) |

One row per product (123 rows total).

---

## Key Notes

- **Currency**: PLN (Polish Zloty)
- **Granularity**: Monthly time series, product-level
- **Products**: 123 unique products (P001–P123)
- **Inventory_level = 0** may indicate a stockout event
- Sales and inventory data are interleaved (two rows per product per file)
- The financial plan provides annual aggregated targets that can serve as benchmarks or additional features
