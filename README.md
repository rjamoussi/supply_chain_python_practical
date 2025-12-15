# The Problem - Strategic Asset Production Plan
The new demand forecast and projected orders for the next 5 years just arrived. In order to ensure our companies success, we need to assess the capability of our existing supply chain to meet the forecasted demand.

If we are able to see any issues with the given production plan, we need to come up with mitigating actions in order to ensure we can supply our end customers reliably throughout the entire time horizon.

In order to run this analysis, you are given these 5 data sets:

## 1. asset_uptime.json
This data set contains the runtime and staffing information of each asset. The columns are described below:
   - asset_id: the asset this record refers to.
   - days_per_week: how many days per week this asset is staffed.
   - weeks_per_year: how many weeks per year this asset is staffed.
   - hours_per_shift: how many hours each shift on this asset lasts.
   - shifts_per_day: how many shifts this asset runs per day.

## 2. asset_rates.json
This data set describes the asset performance and contains the following columns:
   - asset_id: the asset this record refers to.
   - Product: the product this record refers to.
   - run_rate: the run rate in units/hour of this product on the asset.
   - cleanup_time: the amount of time [in hours] needed to cleanup the asset after a batch of this product is run (more on this later). This time is incurred after every batch of product.

## 3. skus.json
This data set describes the lot sizing for each sku. A lot size is the amount of units that make up a batch. When a complete batch is run on a line, a cleanup must be done which takes the amount of time outlined in **asset_rates.cleanup_time**.

in summary: batches = (units / lot_size). Batches always round up to ensure our lines are in running shape. The columns in this dataset are as follows:
   -  Product: the product this record refers to.
   -  Lot Size: the amount of units per batch.

## 4. orders.json
This data set contains the projected orders from 2025-2030. The columns are as follows:
   - proj_id: the projected order ID.
   - Year: the year in which the order needs to be filled.
   - Month: the month in which the order needs to be filled.
   - SKU: the Product that the order is for.
   - Demand: the amount of units this order calls for.

### 5. allocation_plan.json
This data set contains the initial proposed plan to meet demand from 2025-2030. This is the plan that needs to be vetted for feasibility and mitigating actions. This data set contains the following columns:
   -  Asset: The asset slated to fill the order.
   -  proj_id: The order to be put on the asset.
