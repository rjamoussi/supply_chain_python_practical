Welcome to the python practical!

The goal of this practical is to assess your python proficiency and problem solving skills. It is expected that you will only use python to achieve the task below. During the interview, you will be given time to:
1. 5 Minutes to explain your findings and any recommendations (if there are any).
2. 10-15 minutes to answer questions regarding your code and your approach to solving the issue. Code based questions may be (but will not be limited to):
  - How did you set up your environment?
  - Did you use any packages to solve the problem? Which ones and why?
  - Q's around code organization, style, and function.

It is okay to use any resources you may need to solve this problem, but remember that you will be thoroughly questioned about the solution and your understanding of the process & code used to arrive at the solution.

You may be wondering why I provided you the data in the format that I did. While I can't stop you from converting things into excel/csvs - That is not the point of this practical. I'd appreciate it if you used python entirely in order to solve this problem.

The datasets (which will be described later) are provided in JSON files oriented as a list of records where each record is a row of data - for example:
```
data = [{column: value, column, value, ..}, ...]
```

All work should be done in the same directory as the datasets. You can manipulate the provided data sets in any way you'd like to arrive at a solution.

*If you are unable to make progress on the problem after some point, that is okay! Please just give it your best shot and do as much as you can do and outline difficulties you had in the process!*

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


# The Solution

A good solution should contain the following:
1. At least one visualization (made using python) of the current production plan that outlines any nuances or issues with the plan that need to be brought to the attention of senior leadership.
2. A description of any recommended actions needed to mitigate any issues with the current production plan.

- Note: The solution should be given using **annual grain of data**. All outputs should be visualized on an annual basis, not monthly.

Feel free to add any more detail if you feel it is needed. You will have no more than 5 minutes to go over the above 2 points in the interview.

**Please be sure to submit your solution to Anthony Del Russo [anthony.del.russo@merck.com](mailto:anthony.del.russo@merck.com?subject=Code_Submission) either in the form of a Zip file or a link to a GitHub page.**