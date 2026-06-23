# Customer Lifecycle & Retention Analysis

## Project Background
This project analyzes data from Voltix Electronics, an online store that sells consumer electronics through its website and mobile app worldwide. The company collects a lot of data about user actions, but this information was not fully utilized before.

This study thoroughly analyzes and synthesizes granular user event log data to discover critical operational insights and enhance the company's overall commercial success. We look past the high sales numbers to find exactly where and why users leave the platform.

The analysis focuses on three practical areas:
* Conversion Funnel: Finding the exact steps where users drop off between viewing a product and buying it.
* Cohort Retention: Tracking how long users stay active and loyal week after week.
* High-Level KPIs: Evaluating total revenue, order volume, and average order value to see if current business growth is stable for the future.

Project Resources:
* **Interactive Power BI Dashboard:** Can be downloaded [here](https://drive.google.com/file/d/1JD-_kn0LZ-Lgb8KgNAaVNJqV9bxQVIf8/view?usp=sharing).
* **Data Preparation & ETL:** The Google Colab file with data cleaning, organization, and preparation for the dashboard can be found [here](https://colab.research.google.com/drive/1R7rnS4ImP236Z7N_vgET2rEogYDIB_qu?usp=sharing).

## Data Structure & Initial Checks
The dataset for Voltix Electronics contains user interaction logs. It consists of a single table tracking individual event history with a total of **885,129 rows** spanning over **157 days** (from September 24, 2020, to February 28, 2021).

<table>
  <thead>
    <tr>
      <th align="left">Column Name</th>
      <th align="left">Data Type</th>
      <th align="left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><b>event_time</b></td>
      <td>datetime</td>
      <td>Corrected timestamp of the user action (UTC)</td>
    </tr>
    <tr>
      <td><b>event_type</b></td>
      <td>string</td>
      <td>Type of action: view, cart, or purchase</td>
    </tr>
    <tr>
      <td><b>product_id</b></td>
      <td>string</td>
      <td>Unique identifier for the product</td>
    </tr>
    <tr>
      <td><b>category_id</b></td>
      <td>string</td>
      <td>Unique identifier for the product category</td>
    </tr>
    <tr>
      <td><b>category_code</b></td>
      <td>string</td>
      <td>Category taxonomy (e.g., electronics.telephone)</td>
    </tr>
    <tr>
      <td><b>brand</b></td>
      <td>string</td>
      <td>Brand name of the product</td>
    </tr>
    <tr>
      <td><b>price</b></td>
      <td>float</td>
      <td>Price of the item in USD</td>
    </tr>
    <tr>
      <td><b>user_id</b></td>
      <td>string</td>
      <td>Unique identifier for the customer</td>
    </tr>
    <tr>
      <td><b>user_session</b></td>
      <td>string</td>
      <td>Unique identifier for the user's browser session</td>
    </tr>
  </tbody>
</table>

### Data Preparation Workflow
Before building the dashboard, the raw data was processed to ensure accurate results. This preparation included editing column data types, removing duplicate rows, and structuring the data specifically for cohort analysis.

The complete Python script with the cleaning and data preparation workflow can be reviewed [here](https://colab.research.google.com/drive/1R7rnS4ImP236Z7N_vgET2rEogYDIB_qu?usp=sharing).

## Executive Summary

### 1. High-Level KPIs vs. Product Reality
At first glance, the top-level financial metrics show strong performance. The platform looks highly successful with **$5.13M in total revenue**, **24,34K completed orders**, and a solid average order value (**AOV of $210.54**). 

<img width="971" height="174" alt="image" src="https://github.com/user-attachments/assets/8205e3af-eb81-4a00-abf0-b30a4e9762c5" />

However, these high sales figures create a false sense of security. To understand the true health of the business, we need to look "under the hood" at how users actually move through the platform.


### 2. Conversion Funnel & Retention Trends

<img width="1369" height="460" alt="image" src="https://github.com/user-attachments/assets/f20059df-de19-41b6-9828-465b9bb18768" />

When analyzing the conversion funnel and the overall retention trend, we see that the majority of users drop off almost immediately:
* **The Main Funnel Leak:** There is a critical drop-off between viewing a product and adding it to the cart. Only **9.08%** of users who view an item ever add it to their shopping cart. 
* **Final Purchase Rate:** Ultimately, only **5.24%** of users complete a purchase from their initial view.
* **The Retention Trend:** The weekly retention line chart confirms this systemic issue. User return rates drop sharply after the first week and continuously sit far below the healthy e-commerce market benchmark of **20%**.
      <td style="padding: 8px; border-bottom: 1px solid #E0EDEA; color: #4A7066;">string</td>
      <td style="padding: 8px; border-bottom: 1px solid #E0EDEA;">Unique identifier for the user's browser session</td>
    </tr>
  </tbody>
</table>

### 3. Cohort Retention Matrix Analysis
<img width="1247" height="550" alt="image" src="https://github.com/user-attachments/assets/51cb4557-3273-4dd4-9b92-2032cecb1517" />

A detailed look at the weekly tracking highlights a severe problem with user loyalty across all periods:
* **The Drop-Off:** In Week 1, retention across almost all cohorts plummets down to 2.5% – 3.5%. This means the platform loses around 97% of its newly acquired customers within the first 7 days.
  
* **The September 21 Exception:** The cohort from September 21, 2020, stands out with the highest Week 1 retention rate at **5.6%**. This anomaly indicates a significantly more effective marketing campaign or higher-quality user acquisition during that specific week.
  
* **The "Dead" Matrix:** While some minimal user activity slowly decays over the first two months, every single cohort effectively flattens out and "dies" (dropping to a critical 0.1% – 0.2%) **after week 10**.
  
* **The Verdict:** The business operates like a "leaky bucket." While marketing successfully brings in new users and generates high initial revenue, the product fails to retain them, resulting in zero long-term customer loyalty.

## Actionable Recommendations

Based on the findings, the company needs to shift its focus from aggressive new user acquisition to fixing user experience friction and building retention. 

### 1. Optimize the User Experience (Product & UI/UX Team)
* **Fix the Funnel Leak:** With only 9.08% of users adding items to the cart, the team must review the product description pages. We need to identify technical bugs, optimize page loading speed, and simplify the "Add to Cart" button visibility.
  
* **Streamline the Checkout Process:** Ensure that the path from cart to purchase is as short and seamless as possible to push the final 5.24% conversion rate higher.

### 2. Implement Retention Strategies (Marketing Team)
* **First-Week Activation:** Since the platform loses around 97% of users within the first 7 days, it is critical to launch automated email/push campaigns or discount offers within 48 hours of their first view to drive them toward a second action.
  
* **Analyze the September 21 Success:** Investigate what specific marketing channels, ad creatives, or promotional offers were used during the week of September 21, 2020. Replicating this strategy can help increase overall baseline Week 1 retention.
  
* **Introduce Loyalty Programs:** Create post-purchase retention mechanics (e.g., cashback, loyalty points, or special discounts on the next purchase) to transform one-time buyers into active, long-term cohorts.

---

👉 **Ready to see the visual insights?** [Click here to review Power BI Dashboard](https://drive.google.com/file/d/1JD-_kn0LZ-Lgb8KgNAaVNJqV9bxQVIf8/view?usp=sharing).
