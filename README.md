# Stochastic Inventory Optimization Simulation

## Overview
This project bridges technical programming with supply chain management by simulating a continuous review $(s, Q)$ inventory policy under real-world uncertainty. Relying on static averages for customer demand and supplier lead times often leads to stockouts and ballooning costs. This Python-based Monte Carlo simulation stress-tests inventory parameters against stochastic volatility.

## The Business Problem
Many operations rely on static EOQ (Economic Order Quantity) and ROP (Reorder Point) models. However, when daily demand fluctuates and suppliers experience delays, lean inventory systems fracture. The goal of this simulation is to programmatically find the optimal balance between **Holding Costs** (tying up capital) and **Stockout Costs** (lost sales).

## Technical Implementation
* **Language:** Python
* **Libraries:** `numpy` (for stochastic distribution generation), `pandas` (for data structuring), `matplotlib` (for KPI visualization).
* **Mechanics:** The model runs a 365-day loop. It uses normal distributions to generate randomized daily demand and delayed lead times, tracking daily inventory levels, pending orders, and total operational costs.

## Key Findings (Before & After)

**1. The "Lean" Trap (Failing Scenario)**
When the Reorder Point was set aggressively low (ROP: 100) to minimize holding costs, the volatility caused the system to crash:
* **Fill Rate:** 78.1%
* **Total Cost:** $65,646 (Driven heavily by stockout penalties)

**2. The Optimized Model**
By adjusting the Reorder Point to absorb the calculated standard deviations of demand and lead time (ROP: 250), the system stabilized:
* **Fill Rate:** 97.8%
* **Total Cost:** $47,340
* **Impact:** Reduced overall supply chain costs by over 27% while significantly improving customer service levels.

## Files in this Repository
* `inventory_simulation.ipynb`: The core Jupyter Notebook containing the Python simulation loop and visualization code.
* `Failing_Inventory.png`: Visual output of the stockout scenario.
* `Optimized_Inventory.png`: Visual output of the optimized $(s, Q)$ policy.
