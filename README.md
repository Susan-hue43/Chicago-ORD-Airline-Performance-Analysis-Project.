# Chicago-ORD-Airline-Performance-Analysis-Report.

![20250515_1712_Airline Performance Designs_simple_compose_01jva4hv2qf15vfm7vzg85cq5g](https://github.com/user-attachments/assets/90f1fae4-46c6-455a-a55e-7fa00dca9713)
*photo by sora*

## 📑 Table of Contents

* [Introduction](#introduction)
* [Problem Statement](#problem-statement)
* [Methodology](#methodology)
* [Profitability Analysis and Business Case Scenarios](#profitability-analysis-and-business-case-scenarios)

  * [Scenario 1: Most Profitable Routes, Aircraft, Airports, and Flight](#scenario-1-most-profitable-routes-aircraft-airports-and-flight)
  * [Scenario 2: Least Profitable Routes, Aircraft, Airports, and Flights](#scenario-2-least-profitable-routes-aircraft-airports-and-flights)
  * [Scenario 3: Seasonal Flight Volume Trends – Uncovering Demand Patterns Across Most Profitable Routes](#scenario-3-seasonal-flight-volume-trends--uncovering-demand-patterns-across-most-profitable-routes)
  * [Scenario 4: Seasonal Flight Volume Trends – Uncovering Demand Patterns Across Least Profitable Routes](#scenario-4-seasonal-flight-volume-trends--uncovering-demand-patterns-across-least-profitable-routes)
* [Conclusion](#conclusion)
* [Recommendations](#recommendations)

---

## Introduction

This project presents an in-depth analysis of a small startup airline's financial performance across its routes, aircraft, and airport operations. The analysis was commissioned by the CEO to help uncover strategic insights that can guide business growth and improve efficiency. The airline operates out of the Chicago, Illinois area, with a strong foundation in operations but limited experience in financial and data analytics.

Given the fragmented state of the airline’s data systems, this project focuses on consolidating and analyzing disparate data sources to identify the most and least profitable routes, evaluate flight trends, and recommend opportunities for optimization in route planning and resource utilization.

---

## Problem Statement

You are a consultant working with a small startup airline based in the Chicago, Illinois area. While the management team has strong experience in airline operations, they lack financial and data analytics expertise. Additionally, the company’s operational data is spread across multiple unconnected systems, making it difficult to extract meaningful insights efficiently.

For example, details such as aircraft type, route assignments, and seating capacity previously required manual comparison across multiple files. Recognizing these limitations, the CEO has requested a comprehensive financial analysis to consolidate insights from various sources and uncover actionable trends that can support data-driven decision-making and help the airline strengthen its market position.

---

## Methodology

This analysis was conducted in **Microsoft Excel**, with **Power Query** used for integrating and transforming fragmented data, and **Pivot Tables** for summarization and trend analysis.

The startup airline faced a major challenge: key data on **aircraft, routes, flights, and financials** was spread across **unlinked sheets** in the Excel workbook **`GTP Case week 3.xlsx`**, making it difficult to extract insights.

To address this, Power Query was used to **consolidate and relate the separate datasets**. As shown in the **Power Query Editor screenshot** below, the **Queries pane** lists multiple initial queries (e.g., `AircraftPivot`, `AirportPivot`, `FlightsPivot`, `RoutesPivot`), each representing a distinct sheet from the workbook. The **formula bar confirms** the merging via the **Primary key & Foreign Key** of primary and secondary table respectively.

<img width="960" alt="image" src="https://github.com/user-attachments/assets/96de96db-90a7-43dc-bbf6-2600ade67c32" />

The consolidation process involved **sequential merging of queries using Power Query's "Merge Queries" feature**:

* Queries like `Flights_Routes` resulted from joining “Flights” and “Routes” using a shared key such as `RouteID`.
* `Flights_Routes_Aircraft` suggests a further merge with “Aircraft” data via `AircraftID`.

These joins created **composite queries**, enabling row-by-row linkage of related data. The resulting **unified data model** allowed for:

* Consistent and dynamic analysis via Pivot Tables.
* Clear insights into **revenue, profitability, flight volume, delays, and capacity.**

Below are the tables used in the analysis, each with its respective columns and descriptions:


#### **Airports Table**

| **Column**                    | **Description**                          |
| ----------------------------- | ---------------------------------------- |
| `AirportID`                   | Unique identifier for each airport       |
| `AirportName`                 | Name of the airport                      |
| `Gates (number of available)` | Number of gates available at the airport |


#### **Aircraft Table**

| **Column**                      | **Description**                                     |
| ------------------------------- | --------------------------------------------------- |
| `AircraftID`                    | Unique identifier for each aircraft                 |
| `AircraftType`                  | Model or type of aircraft                           |
| `SeatCapacity`                  | Number of passenger seats available                 |
| `FuelCostperSeatMile (Cents)`   | Fuel cost per seat per mile (in cents)              |
| `FuelCostperSeatMile (Dollars)` | Fuel cost per seat per mile (in dollars)            |
| `FuelCostperMile (Dollars)`     | Total fuel cost per mile (regardless of passengers) |


#### **Routes Table**

| **Column**   | **Description**                     |
| ------------ | ----------------------------------- |
| `DepAirport` | Departure airport identifier        |
| `AirportID`  | Destination airport identifier      |
| `Distance`   | Distance of the route (in miles)    |
| `ListPrice`  | Standard ticket price for the route |


#### **Flights Table**

| **Column**            | **Description**                                |
| --------------------- | ---------------------------------------------- |
| `FlightID`            | Unique identifier for each flight              |
| `Date`                | Date the flight took place                     |
| `RouteID`             | Identifier linking to the route flown          |
| `Departure Delay`     | Minutes of delay at departure                  |
| `AircraftID`          | Identifier of the aircraft used                |
| `Scheduled Departure` | Planned time of departure                      |
| `Avg Ticket Price`    | Average ticket price per passenger             |
| `Total Fare`          | Total revenue from ticket sales for the flight |
| `Flight Month`        | Month of the flight (used for trend analysis)  |
| `Flight Year`         | Year of the flight                             |
| `Revenue per flight`  | Total revenue earned for the specific flight   |

---

## Profitability Analysis and Business Case Scenarios.

**Analysis:**
Our analysis of where we made and lost money is based on **profit**, calculated by subtracting **fuel costs** from **total revenue**. Since fuel cost was the only provided expense factor, we used it as the primary cost element in evaluating profitability. By comparing revenue generated from each **route**, **airport**, and **aircraft** against their respective fuel costs, we were able to identify both **high-performing** and **underperforming** areas within the business.

To bring these insights to life, we developed a series of **case scenarios**, each answering a specific business question using available data.

---

## Scenario 1: Most Profitable Routes, Aircraft, Airports, and Flight.
### 1.1 Most Profitable Routes.
![image](https://github.com/user-attachments/assets/f9f14809-c121-4413-9a82-f767de1f8784)

#### **Observation and Impact**

* **Highest Profit Routes.**
Routes from Chicago O’Hare (ORD) to Los Angeles (LAX), San Francisco (SFO), and Denver (DEN) generate the highest total profits per flight. Notably, **ORD–LAX** leads with a total profit of **\$42.7 million** across **699 flights**, followed by **ORD–SFO** at **\$39.0 million** over **604 flights**, and **ORD–DEN** at **\$33.2 million** with **614 flights**.

  **Impact:** These routes are critical revenue drivers, meaning the airline’s overall profitability is heavily reliant on their continued strong performance and demand stability.

* **Moderate-to-High Flight Volume, Mid-Level Profit.**
Routes from Chicago O’Hare to Atlanta (ATL), Dallas/Fort Worth (DFW), New York John F. Kennedy (JFK), and Miami (MIA) operate with a high number of flights ranging from **455 to 762** but show comparatively moderate total profits between **\$24.1 million and \$29.4 million**.

  **Impact:** High operational activity with only moderate returns may indicate reduced efficiency or pricing pressure, potentially affecting long-term profitability on these routes.

* **Low Flight Volume, High Profit Efficiency.**
Routes such as Chicago O’Hare to Washington National (DCA) and Seattle (SEA) demonstrate high total profit relative to flight volume. **ORD–DCA**, with just **24 flights**, generates an impressive **\$21.8 million**, while **ORD–SEA** achieves **\$25.7 million** over **421 flights**.

  **Impact:** These routes exhibit strong profit efficiency per flight, suggesting potential for scalable growth or opportunities for reallocating capacity to maximize return.

* **Low Profit and Low Flight Volume.**
Routes such as Chicago O’Hare to Salt Lake City (SLC), Baltimore (BWI), Washington Dulles (IAD), and Minneapolis–St. Paul (MSP) record both low profit (below **\$6.1 million**) and low flight counts (under **300 flights**), indicating minimal overall revenue contribution.

  **Impact:** These routes contribute little to the network’s financial performance and may be deprioritized in terms of investment, scheduling, or strategic expansion efforts.

---

### **1.2. Aircraft Profitability Analysis.**

![image](https://github.com/user-attachments/assets/774bd12c-b216-4abe-ad68-cce035491b98)

![image](https://github.com/user-attachments/assets/82e0641e-c720-4070-b396-56e3d59dd80a)


* **Airbus A320**

  * Carries **181 seats** and records the **lowest total profit** at **\$61.5 million**.
  * Also has the **lowest profit per seat** at **\$261.70**.
  * **Impact:** The A320 appears to be **underperforming** both in total return and per-seat profitability, possibly due to suboptimal route assignments or lower demand efficiency.

* **Airbus A319**

  * Has a smaller capacity of **165 seats**, generating a strong **\$171.0 million** in total profit.
  * Delivers a **profit per seat of \$267.25**, nearly matching the B737.
  * **Impact:** Despite fewer seats, the A319 achieves **high per-seat profitability**, indicating it is **efficiently deployed** and potentially ideal for routes with moderate demand and strong margins.

* **Boeing 737 (B737)**

  * Offers **185 seats**, the largest among the three.
  * Leads with the **highest total profit** at **\$220.6 million** and the **highest profit per seat** at **\$267.48**.
  * **Impact:** The B737 combines **scale and efficiency**, making it the **top-performing aircraft** in both profitability metrics and suggesting strong alignment with high-demand, high-yield routes.

---

### **1.3. Top 10 Airports by Profit.**

![image](https://github.com/user-attachments/assets/176ca3fc-e00c-45c6-b134-76e301f4ecd4)


#### **Observation and Impact**

  * **Top Profit-Generating Destinations by Profit**
Routes from Chicago O’Hare (ORD) to **Los Angeles (LAX), San Francisco (SFO), and Denver (DEN)** deliver the highest profits, with LAX leading at **\$42.7 million**, followed by SFO at **\$39.0 million** and DEN at **\$33.2 million**. These destinations consistently outperform others in terms of per-flight returns.

    **Impact:** These high-profit routes are essential for maximizing profitability, suggesting a need to prioritize capacity, pricing, and service quality on these corridors to sustain financial performance.

  * **Strategically Important Medium-Tier Routes.**
Flights to **New York JFK, Atlanta (ATL), Seattle (SEA), Dallas/Fort Worth (DFW), Miami (MIA), and Las Vegas (LAS)** show solid mid-range profit figures, spanning from **\$24.1 million to \$29.4 million**. While not at the top, these destinations represent a significant portion of ORD’s operational throughput.

    **Impact:** These destinations provide a stable revenue base. Monitoring cost efficiency, seasonal demand shifts, and pricing strategy could unlock further value.

  * **High Efficiency, Niche Opportunity Route.**
The ORD–Washington National (DCA) route, though likely operating at lower frequency, achieves an impressive **\$21.8 million** in profit nearing the top 10 threshold.

    **Impact:** Despite its relatively lower volume, this route delivers outsized returns and may represent an underutilized opportunity for expanding high-margin operations.

---

### **1.4. Top Earning Flights.**

![image](https://github.com/user-attachments/assets/51081414-da2e-480e-aee2-858adb78cdef)


#### **Observation and Impact**

* **Top Earning Flights by Individual Profit.**

  Multiple flights:-**Flight6243, Flight8279, Flight1819, and Flight8202** tie for the highest profit at **\$1.02 million** each, indicating consistent high-performing services. These may reflect high-demand or premium routes, possibly with optimized pricing or strong load factors.

  **Impact:** These top-grossing flights are likely central to maximizing profitability at the flight level. Ensuring operational reliability and customer satisfaction on these flights is essential to maintaining their high revenue contribution.

* **Mid-Tier Profit Flights with Strong Potential.**
  
  Flights such as **Flight7316 (\$993K)** and several others **Flight1580, 3769, 2232, 1449, and 2466** earn between **\$922K and \$993K**, showing strong revenue but slightly lower than the top performers.

  **Impact:** These flights present opportunities for incremental improvement through fare optimization, ancillary revenue, or better seat utilization to elevate them into the top tier of performance.

---

## Scenario 2: Least Profitable Routes, Aircraft, Airports, and Flights. 

**Where Are We Losing the Most Money?**
Despite some profitable routes, certain routes and operational factors result in significant losses.  

### 2.1. **Least Profitable Routes.**

![image](https://github.com/user-attachments/assets/cadfb622-2de8-4b18-80f1-2e0a84e2e357)

#### **Observations and Impact**
* The **least profitable route**, **ORD–SLC (\$1.84M over 36,000 miles)**, generates minimal return despite its relatively short distance, suggesting low demand or uncompetitive pricing.

  **Impact:**
   This underperformance raises questions about market viability continued service may need justification through strategic value, not financial return alone.

* Routes like **ORD–BWI (\$4.44M)** and **ORD–IAD (\$4.68M)** also have **modest distances (45K–54K miles)** and low profit, pointing to a pattern of weak returns on short to mid-haul East Coast routes.

  **Impact:**
   This trend suggests that short-haul routes may suffer from high competition or insufficient pricing power, warranting pricing strategy reviews or reduced frequency.

* **ORD–DTW** and **ORD–MSP** show **low profits (\$5.8M–\$6.1M)** despite flying **moderate distances (56K–89K miles)**, indicating possible issues with load factors or overcapacity.

  **Impact:**
   These may be candidates for aircraft right sizing or schedule adjustments to improve efficiency and yield per flight.

* **ORD–FLL**, at **139K miles**, is a longer route yet still ranks among the bottom 10 with only **\$7.9M** in profit suggesting distance alone doesn’t drive profitability.

   **Impact:**
   Low return on a long-haul route may indicate pricing misalignment with cost structure or underperformance during off-peak seasons. Closer scrutiny of seasonal and demand patterns is advised.

*  Higher distance routes like **ORD–CLT (399K miles)**, **ORD–IAH (357K)**, and **ORD–MCO (300K)** deliver **moderate profits (\$12M–\$15.7M)** but still fall behind the top earners.

   **Impact:**
   While better than others in this tier, these routes may have room for improvement in upselling premium services, managing operational costs, or optimizing fare classes.

* Overall, these **10 least profitable routes** cover **1.66 million miles** and generate a combined **\$89.7 million**, averaging **\$54 per mile** below the benchmark set by more profitable routes.

  **Impact:**
  These results suggest that **route underperformance is influenced by both travel distance and demand quality**. Enhancing cost-efficiency, pricing, or scheduling on lower-yielding routes could raise the average profit generated per mile throughout the network.

---

### 2.2. Least Profitable Aircraft.

![image](https://github.com/user-attachments/assets/3b2ad5f4-52b2-43d2-821a-b92cbb397a11)

#### **Observations and Impact**
*  The **A320** has the **lowest fuel cost per flight (\$4.15M)** while still generating a strong **total revenue of \$65.6M**, suggesting higher fuel efficiency and better profit margins.

   **Impact:**
   This aircraft appears to be the most cost-effective in the current fleet and may be prioritized for expansion on profitable or growing routes.

* The **A319** incurs a **fuel cost of \$10.62M** with a **total revenue of \$181.7M**, indicating moderate fuel efficiency.

  **Impact:**
   While performance is acceptable overall, route-specific analysis may identify low-efficiency pairings. There may be potential for operational gains by shifting to more efficient aircraft where viable.

* The **B737**, though generating the highest **total revenue (\$235.6M)**, also consumes the most fuel (**\$14.99M**), which dilutes per-flight profitability.

  **Impact:**
   This suggests that despite strong revenue generation, the B737’s higher operating costs could reduce margins. The airline should evaluate whether its deployment justifies the cost or whether more efficient aircraft can be used for select routes.

* Comparing the three, **fuel cost per dollar earned** is highest for the B737, followed by the A319, then the A320 indicating that **the A320 is the most fuel-efficient relative to revenue**, while **the B737 is the least efficient**.

  **Impact:**
   Strategic fleet planning should consider reallocating B737 usage to high-demand, long-haul routes where its capacity offsets cost, and prioritizing A320s for routes where margin is more sensitive to fuel expense.

---

### 2.3. **Least Profitable Destination Airports.**

![image](https://github.com/user-attachments/assets/2b784625-30de-4445-8c21-9edfe7c9331e)

#### **Observations and Impact**
*   **Salt Lake City International (SLC)** is the **least profitable airport**, generating only **\$1.84M**, which aligns with its corresponding route's low efficiency.

    **Impact:**
   SLC’s poor performance suggests limited demand or high operational costs warranting reassessment of service levels or pricing models on this route.

* **Baltimore/Washington (BWI)** and **Washington Dulles (IAD)** follow closely behind with **profits under \$5M** each, despite being major hubs.

  **Impact:**
   These results may indicate route saturation, fare pressure, or underutilized flights. Targeted marketing or capacity adjustments may improve yields.

*  **Detroit (DTW)** and **Minneapolis-St. Paul (MSP)** generate **profits just above \$5M and \$6M**, respectively low figures given their relatively short distances from ORD.

   **Impact:**
   These short-haul routes may be suffering from high frequency with low fare returns. A shift in aircraft or frequency reduction could boost profitability.

*  **Fort Lauderdale (FLL)** ranks mid-tier in this group at **\$7.9M**, indicating better seasonal or tourist-driven profitability but still lower than top-tier routes.

   **Impact:**
   With targeted promotions and better flight timing, FLL could move into a higher profit tier—especially during peak travel periods.

*  **Charlotte (CLT), Philadelphia (PHL), Houston (IAH), and Orlando (MCO)** all generate profits **above \$11M**, suggesting stronger load factors or optimized pricing despite longer distances.

   **Impact:**
   These airports are performing relatively well compared to others in this group and may warrant further investment in frequency or premium services.

---

### 2.4. **Least Profitable Flights.**

![image](https://github.com/user-attachments/assets/d2098dee-3810-4720-b698-ebb5d7e4b2e4)


#### **Observations and Impact**
* All listed flights such as **Flight 1088, 5525, and 6769** generate profits of only **\$17.8K–\$17.9K per flight**, which is considerably lower than high-performing flights exceeding \$1M.

  **Impact:**
   These flights represent a poor return on operational effort. Their low profit per flight could strain network profitability if not offset by high-performing routes.

* A pattern emerges in the **average ticket price**, ranging from **\$115 to \$125**, suggesting uniformly low fares across all these flights.

   **Impact:**
   Such pricing may not sufficiently cover operational costs, especially for flights with lower load factors or inefficient aircraft use. Fare adjustments or demand stimulation may be necessary.

* The consistency of profits and fares implies these may be **short-haul or regional flights** where pricing is constrained, or competition drives down fares.

  **Impact:**
   These routes may benefit from dynamic pricing strategies, ancillary revenue increases, or potential bundling offers to improve financial performance.

* The similarity in financial performance across flights suggests a **structural issue** possibly aircraft assignment, scheduling inefficiencies, or underperforming markets.

  **Impact:**
   Reassessing aircraft utilization, route timing, or even consolidating underperforming frequencies may enhance route-level profitability.

---

## **Scenario 3: Seasonal Flight Volume Trends – Uncovering Demand Patterns Across Most Profitable Routes.**

![image](https://github.com/user-attachments/assets/53268964-c3e6-4188-bfc4-eefc5217852d)


### **3.1. Peak Flight Volume Months:**

* **August & November (2014):** 159 and 167 flights
* **June & July (2015):** 137 and 138 flights

  **Impact:** These months show the highest flight volumes in both years, underlining peak summer travel demand. These are critical for capacity planning, as they directly correlate to revenue opportunities due to high demand.


### **3.2. Lowest Flight Volume Months:**

* **April & May (2014):** 80 flights each
* **September (2015):** 81 flights

  **Impact:** These months represent off-peak periods, where lower flight volumes can result in reduced profitability. Airlines should consider using this data for targeted promotions, fare discounts, or aircraft maintenance scheduling to maintain profitability without reducing flight frequencies.


### **3.3. Total Yearly Flight Volumes:**

* **2014:** 1,378 flights
* **2015:** 1,340 flights

  **Impact:** The stable yearly volume metric reflects consistent demand patterns, but the slight decline in 2015 (compared to 2014) could be a signal to further assess factors influencing demand and consider adjustments in pricing or capacity to maintain growth.


### **3.4. Monthly Flight Count Average (Over Two Years):**

* **Average Monthly Flights:** 113 (Based on 2,718 total flights across both years)

  **Impact:** The average monthly flight volume provides a baseline for expected activity, helping in forecasting, budget allocation, and operational optimization. Deviation from this average in specific months (e.g., July, August, and the slower months) can help refine performance expectations.

Here’s a structured version of your analysis for the **least profitable routes (SLC, BWI, IAD, DTW, MSP, FLL)** using the same format and tone as the one used for the most profitable routes:

---

## **Scenario 4: Seasonal Flight Volume Trends – Uncovering Demand Patterns Across Least Profitable Routes.**

![image](https://github.com/user-attachments/assets/a0d6fb0b-6cd5-474a-9aca-7e1f58c1e65f)

### 4.1. Peak Flight Volume Months:

* **June & August (2014):** 58 and 51 flights.
* **June, August & September (2015):** 47 and 46 flights.

  **Impact:** These summer months show the highest flight volumes across both years, signaling that even underperforming routes experience seasonal spikes. However, the lack of corresponding profitability indicates that **high demand does not always equate to high-margin traffic**. These months are critical for reviewing **pricing strategies and aircraft utilization** to convert volume into margin.

### 4.2. Lowest Flight Volume Months:

* **February (2014):** 28 flights.
* **October (2014):** 26 flights.
* **October (2015):** 30 flights.

  **Impact:** These off-peak periods reveal dips in traffic and are potential contributors to weak overall performance. Airlines could use these windows for **targeted promotions**, **tactical route reductions**, or **maintenance scheduling** to minimize losses without fully exiting the route.


### 4.3. Total Yearly Flight Volumes:

* **2014:** 486 flights.
* **2015:** 464 flights.

  **Impact:** The relatively consistent flight volumes year-over-year suggest **stable operational commitment** despite financial underperformance. This consistency emphasizes the need to address **route-level inefficiencies**, rather than reduce flying, especially if these routes are strategically important for network coverage.


### 4.4. Monthly Flight Count Average (Over Two Years):

* **Average Monthly Flights: 79** (Based on 950 total flights over 24 months)

  **Impact:** This monthly average is lower than the network-wide norm, underscoring that these routes operate at **sub-scale levels**, which can hinder economies of scale. Comparing actual monthly volumes to this benchmark can help in deciding **where to consolidate or scale**.

---

## **Conclusion and Recommendations**

## **Conclusion**

The airline's route and operational profitability analysis reveals a concentrated dependency on a few high-performing routes, aircraft, and destinations. Routes from Chicago O’Hare (ORD) to Los Angeles (LAX), San Francisco (SFO), and Denver (DEN) consistently emerge as top revenue generators, delivering the highest total profits per flight. Aircraft-wise, the Boeing 737 leads in overall profitability, while the Airbus A320 offers the most fuel-efficient returns relative to revenue.

Conversely, several short- and mid-haul routes such as ORD–SLC, ORD–BWI, and ORD–IAD are underperforming significantly, both in profit and flight efficiency. These routes, along with the corresponding airports, contribute minimally to network profitability. Operational costs, particularly fuel usage for the B737, reveal that high revenue does not always equate to optimal margin, underlining the importance of fuel efficiency and route alignment.

This profitability disparity highlights the need for strategic resource allocation, efficiency improvements, and tailored pricing strategies to ensure sustainable growth and margin improvement across the network.

---

## **Recommendations**

#### 1. **Prioritize and Expand High-Performing Routes**

* **Maintain and potentially increase frequency** on high-profit routes such as ORD–LAX, ORD–SFO, and ORD–DEN to maximize revenue.
* **Enhance pricing strategies and customer experience** on these routes to retain competitive advantage and yield premium returns.

#### 2. **Reallocate Capacity from Low-Performing Routes**

* **Review route viability** for consistently underperforming corridors like ORD–SLC, ORD–BWI, and ORD–IAD. Consider reducing frequency, rerouting, or exiting where strategic justification is weak.
* **Implement route-level cost controls** and assess demand elasticity to test revised schedules or smaller aircraft on marginal routes.

#### 3. **Optimize Aircraft Deployment**

* **Assign B737s to long-haul, high-demand routes** where their higher capacity justifies fuel and operating costs.
* **Utilize A320s more strategically** on medium-haul, cost-sensitive routes to benefit from their superior fuel efficiency relative to revenue.
* **Continue leveraging the A319** on routes with moderate traffic and strong profit-per-seat margins.

#### 4. **Enhance Mid-Tier Route Profitability**

* For routes with high volume but moderate profit (e.g., ORD–ATL, ORD–DFW, ORD–JFK), **evaluate pricing strategies**, fare segmentation, and operational schedules to improve yield.
* **Explore seasonal scheduling and marketing** to optimize demand during off-peak periods.

#### 5. **Target Airport-Specific Strategies**

* **Reassess service to underperforming airports** like SLC, BWI, and IAD, considering demand factors, competition, and cost structures.
* **Focus marketing efforts** and partnerships on improving profitability at mid-tier airports (e.g., FLL, CLT) with potential for seasonal gains.

#### 6. **Monitor and Improve Individual Flight Performance**

* **Track top-grossing individual flights** for operational efficiency and customer satisfaction to preserve and grow profitability.
* **Apply dynamic fare management and ancillary upsells** to elevate mid-tier flights closer to top-performer status.

#### 7. **To improve profitability on underperforming but seasonally active routes,** 

  **consider:**
* **Cost controls** through aircraft type adjustments or staffing alignment.
* **Strategic scheduling** to cut back during inefficient low-demand months.
* **Targeted fare strategies** during peak months to better capture value.
  
---
