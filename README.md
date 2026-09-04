# Blinkit-Delivery-Delay-Root-Cause-Analysis

## Project Overview
Blinkit's key competitive advantage is its **10-minute delivery promise**. This project investigates a significant deterioration in delivery performance and identifies the operational factors contributing to the SLA breach.

The analysis was conducted from the perspective of a **Product Analyst in the Operations Intelligence team**, using operational order, customer-event, and store-load data.

## Business Problem
Delivery times have increased beyond the 10-minute SLA, creating a risk to customer experience and operational efficiency.

The main questions were:
* Is the problem **system-wide or limited to specific zones**?
* When are delivery delays most severe?
* Is the bottleneck caused by **rider capacity or store/picker capacity**?
* Are delays affecting customer cancellations?
* What operational action should Blinkit prioritize?

## Analysis
Using PostgreSQL and SQL, I analyzed:
* Overall delivery performance and SLA breaches
* Zone-level delivery performance
* Hourly delivery trends
* Active orders vs. available riders
* Active orders vs. available pickers
* Customer funnel progression
* Order cancellations

### Key Metrics
**North Star Metric:**
10-Minute SLA Adherence Rate

**Supporting Metrics:**
* Average Delivery Time
* SLA Breach Rate
* Orders per Rider
* Orders per Picker
* Cancellation Rate

## Key Findings
* **96.75%** of orders exceeded the 10-minute SLA.
* Average delivery time was approximately **15 minutes**.
* All four zones experienced significant SLA degradation, indicating a **system-wide problem**.
* Delivery performance deteriorated sharply between **20:00–23:00**, reaching approximately **20 minutes** average delivery time.
* Several zone-hour combinations showed high **orders per rider**, indicating rider capacity pressure.
* North also showed significant **picker pressure**, with **27.67 orders per picker at 23:00**.
* The bottleneck therefore varies by **zone and hour**, rather than being a single network-wide rider shortage.
* The cancellation rate was **1.64%**.
* Weather/rain could not be directly tested because weather data was not available.

## Final Diagnosis
The strongest evidence points to a **late-evening supply-demand capacity imbalance**.
High order volumes during peak hours put pressure on rider and picker capacity, causing delivery performance to deteriorate. The specific constraint varies between zones and operating hours.

## Recommendation
Implement **zone-hour capacity planning** during the **20:00–23:00 peak period**.
* Reallocate riders toward zones with high orders per rider.
* Increase picker coverage where orders per picker indicate store congestion.
* Monitor capacity pressure before the 10-minute SLA begins to deteriorate.
