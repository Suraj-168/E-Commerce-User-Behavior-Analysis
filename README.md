# E-Commerce User Behavior & Funnel Analysis

## Overview
Analysis of user behavior on an e-commerce platform, tracing the full conversion funnel from page view through purchase to identify drop-off points, traffic source performance, and revenue drivers. Built using MySQL and Excel, with results cross-validated between both tools.

## Dataset
About 9,400 events from 5,000 users, covering what action the user took (page view, add to cart, checkout, payment, purchase), where they came from (email, organic, paid ads, social), which product they viewed, how much they paid, and when it happened.

## Data Cleaning
- The amount column was empty for every event except purchases. Filled these empty values with 0, since only a completed purchase actually has a price, and leaving them blank would have caused errors when adding up revenue.
- The event timestamps included very precise fractions of a second, which wasn't needed and made time calculations messier. Cleaned this up so the timestamps could be used properly to measure how long users took between each step.
- Checked the data for duplicate entries and inconsistent labels (like different spellings of the same traffic source). Found none, so no rows had to be removed.

## Tools Used
- MySQL
- Microsoft Excel (Pivot Tables, Charts)

## Analysis Performed
- User funnel analysis (page_view → add_to_cart → checkout_start → payment_info → purchase)
- Traffic source analysis
- Conversion rate analysis (stage-by-stage and overall)
- Product performance
- Revenue analysis
- Customer journey timing (time taken between funnel stages)

## Key Findings
- Email converts best (~34% page view to purchase) despite the lowest traffic volume.
- Social has the weakest top-of-funnel conversion (~13.6% view-to-cart), suggesting a mismatch between social ad creative and actual product pages, not a checkout problem.
- Once a user adds to cart, conversion stays high (70-94%) across all traffic sources. The funnel's biggest leak is at the very first step, not checkout or payment.
- Organic traffic drives the most total revenue (~42%) through volume, even though it doesn't have the highest per-user conversion rate.
- All 6 products convert within a tight 15.5-17.8% range, performance is driven by traffic source, not product.
- Users take the longest to decide whether to add a product to cart (~11.2 minutes on average), more than double the time spent on any later step (5.4 min to checkout, 5.1 min to payment, 3.0 min to purchase). Once a user commits past that point, they move through the rest of the funnel quickly and decisively. This means the page view-to-cart stage is the main friction point in the journey both in terms of who drops off and how long the ones who don't take to decide.
- Total revenue: $87,975.11 across 826 purchases.

## How to Use
1. Open User_Events_Analysis.xlsx to review the Pivot Tables and pre-built conversion/revenue breakdowns.
2. Run the queries in SQL_Queries.sql against a MySQL instance with a matching user_events table to reproduce the results.

## Files
- SQL_Queries.sql
- User_Events_Analysis.xlsx
- user_events.csv (raw data)
