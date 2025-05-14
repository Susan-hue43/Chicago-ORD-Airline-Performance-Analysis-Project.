# Chicago-ORD-Airline-Performance-Analysis-Report.
## Introduction

This project presents an in-depth analysis of a small startup airline's financial performance across its routes, aircraft, and airport operations. The analysis was commissioned by the CEO to help uncover strategic insights that can guide business growth and improve efficiency. The airline operates out of the Chicago, Illinois area, with a strong foundation in operations but limited experience in financial and data analytics.

Given the fragmented state of the airline’s data systems, this project focuses on consolidating and analyzing disparate data sources to identify the most and least profitable routes, evaluate flight trends, and recommend opportunities for optimization in route planning and resource utilization.

---

## Problem Statement

You are a consultant working with a small startup airline based in the Chicago, Illinois area. While the management team has strong experience in airline operations, they lack financial and data analytics expertise. Additionally, the company’s operational data is spread across multiple unconnected systems, making it difficult to extract meaningful insights efficiently.

For example, details such as aircraft type, route assignments, and seating capacity previously required manual comparison across multiple files. Recognizing these limitations, the CEO has requested a comprehensive financial analysis to consolidate insights from various sources and uncover actionable trends that can support data-driven decision-making and help the airline strengthen its market position.

---

## Methodology

This analysis was conducted using **Microsoft Excel**, primarily leveraging **Power Query** for data transformation and Pivot Tables for summarization and trend analysis. The startup airline initially faced a major challenge: data related to aircraft, routes, and financials existed in **separate, unlinked reports**, making it time-consuming to derive insights or generate a single unified report.

To solve this, datasets were **merged using Power Query** based on common identifiers such as `AircraftID`, `AirportID`, and `RouteID`. This allowed for a **consolidated data model**, enabling dynamic exploration and unified insights.

Pivot Tables were then used to perform aggregations and uncover trends related to revenue, profitability, delays, and capacity utilization.

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

### 1. Most Profitable Routes, Aircraft, Airports, and Flight
#### 1.1 Routes
![image](https://github.com/user-attachments/assets/f9f14809-c121-4413-9a82-f767de1f8784)

**Observation and Impact**

* **Highest Profit Routes**
Routes from Chicago O’Hare (ORD) to Los Angeles (LAX), San Francisco (SFO), and Denver (DEN) generate the highest total profits per flight. Notably, **ORD–LAX** leads with a total profit of **\$42.7 million** across **699 flights**, followed by **ORD–SFO** at **\$39.0 million** over **604 flights**, and **ORD–DEN** at **\$33.2 million** with **614 flights**.

  **Impact:** These routes are critical revenue drivers, meaning the airline’s overall profitability is heavily reliant on their continued strong performance and demand stability.

* **Moderate-to-High Flight Volume, Mid-Level Profit**
Routes from Chicago O’Hare to Atlanta (ATL), Dallas/Fort Worth (DFW), New York John F. Kennedy (JFK), and Miami (MIA) operate with a high number of flights—ranging from **455 to 762**—but show comparatively moderate total profits between **\$24.1 million and \$29.4 million**.

  **Impact:** High operational activity with only moderate returns may indicate reduced efficiency or pricing pressure, potentially affecting long-term profitability on these routes.

* **Low Flight Volume, High Profit Efficiency**
Routes such as Chicago O’Hare to Washington National (DCA) and Seattle (SEA) demonstrate high total profit relative to flight volume. **ORD–DCA**, with just **24 flights**, generates an impressive **\$21.8 million**, while **ORD–SEA** achieves **\$25.7 million** over **421 flights**.

  **Impact:** These routes exhibit strong profit efficiency per flight, suggesting potential for scalable growth or opportunities for reallocating capacity to maximize return.

* **Low Profit and Low Flight Volume**
Routes such as Chicago O’Hare to Salt Lake City (SLC), Baltimore (BWI), Washington Dulles (IAD), and Minneapolis–St. Paul (MSP) record both low profit (below **\$6.1 million**) and low flight counts (under **300 flights**), indicating minimal overall revenue contribution.

  **Impact:** These routes contribute little to the network’s financial performance and may be deprioritized in terms of investment, scheduling, or strategic expansion efforts.

---

#### **1.2. Aircraft Profitability Analysis**

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


#### **1.3. Top 10 Airports by Profit.**

![image](https://github.com/user-attachments/assets/176ca3fc-e00c-45c6-b134-76e301f4ecd4)


**Observation and Impact**

  * **Top Profit-Generating Destinations by Profit per Flight**
Routes from Chicago O’Hare (ORD) to **Los Angeles (LAX), San Francisco (SFO), and Denver (DEN)** deliver the highest profits per flight, with LAX leading at **\$42.7 million**, followed by SFO at **\$39.0 million** and DEN at **\$33.2 million**. These destinations consistently outperform others in terms of per-flight returns.

    **Impact:** These high-profit-per-flight routes are essential for maximizing profitability, suggesting a need to prioritize capacity, pricing, and service quality on these corridors to sustain financial performance.

  * **Strategically Important Medium-Tier Routes**
Flights to **New York JFK, Atlanta (ATL), Seattle (SEA), Dallas/Fort Worth (DFW), Miami (MIA), and Las Vegas (LAS)** show solid mid-range profit per flight figures, spanning from **\$24.1 million to \$29.4 million**. While not at the top, these routes represent a significant portion of ORD’s operational throughput.

    **Impact:** These routes provide a stable revenue base. Monitoring cost efficiency, seasonal demand shifts, and pricing strategy could unlock further value.

  * **High Efficiency, Niche Opportunity Route**
The ORD–Washington National (DCA) route, though likely operating at lower frequency, achieves an impressive **\$21.8 million** in profit per flight—nearing the top 10 threshold.

    **Impact:** Despite its relatively lower volume, this route delivers outsized returns and may represent an underutilized opportunity for expanding high-margin operations.

#### **1.4. Top Earning Flights.**

![image](https://github.com/user-attachments/assets/51081414-da2e-480e-aee2-858adb78cdef)


**Observation and Impact**

* **Top Earning Flights by Individual Profit**

Multiple flights:-**Flight6243, Flight8279, Flight1819, and Flight8202** tie for the highest profit at **\$1.02 million** each, indicating consistent high-performing services. These may reflect high-demand or premium routes, possibly with optimized pricing or strong load factors.

  **Impact:** These top-grossing flights are likely central to maximizing profitability at the flight level. Ensuring operational reliability and customer satisfaction on these flights is essential to maintaining their high revenue contribution.

* **Mid-Tier Profit Flights with Strong Potential**
Flights such as **Flight7316 (\$993K)** and several others **Flight1580, 3769, 2232, 1449, and 2466** earn between **\$922K and \$993K**, showing strong revenue but slightly lower than the top performers.

  **Impact:** These flights present opportunities for incremental improvement through fare optimization, ancillary revenue, or better seat utilization to elevate them into the top tier of performance.

---

### Least Profitable Routes, Aircraft, Airports, and Flights 
**2. Where Are We Losing the Most Money?**
Despite some profitable routes, certain routes and operational factors result in significant 
losses.  
  * The least profitable route is **Chicago O'Hare International Airport to Salt Lake City 
International (ORD-SLC)**, which generated a **profit** of only **$1,841,044.90.**  
  * Chicago O'Hare International Airport to Baltimore/Washington International Thurgood 
Marshall **(ORD-BWI) ($4,442,184.91)** and Chicago O'Hare International Airport to 
Washington Dulles International **(ORD-IAD) ($4,676,982.26)** are also among the 
least profitable routes. 
  * The **A319** and **B737** aircraft incur significantly higher fuel costs per flight relative to 
their total fares, which contributes to lower profitability compared to the **A320.** 
  * Salt Lake City International **(SLC)** is the least profitable airport generating **$1.8M** 
significantly trailing behind other airports. 
  * The top flight for this group, **Flight 1088**, generates just **$17,820.60** in **profit** per 
flight, highlighting the inefficiency of these specific routes.

**Conclusion:** While the airline still generates profit from these routes, high fuel costs 
relative to revenue are significantly impacting profitability, especially for shorter and 
medium-haul routes. Optimizing fuel usage and reassessing pricing strategies could 
help reduce losses and improve profitability on these routes. 

---

### Flight Volume Analysis.
**3. How many flights are flown from O'Hare (ORD) to Los Angeles International Airport (LAX)?**
  * The Chicago O'Hare International to Los Angeles International **(ORD-LAX)** route operates **699** flights, highlighting significant demand.

**4. What was the most popular month to fly to Fort Lauderdale (FLL)?**
  * **August** recorded **1,025 flights**, making it the busiest month for this route.

---

### Revenue Contribution by Route.
**5. Which route accounts for the lowest percentage of total revenue?**
  * The route with the **lowest** percentage of total revenue is **Chicago O'Hare International Airport to Salt Lake City International (ORD-SLC)**, accounting for just **0.41%** of the total fare. 
  * Other low-revenue routes include ORD-Baltimore/Washington International Thurgood Marshall **(ORD-BWI) (0.96%)** and ORD-Washington Dulles International **(ORD-IAD) (1.00%)**. These routes contribute **minimally** to the **airline's overall revenue** compared to **high-revenue routes** like ORD-Los Angeles International **(ORD-LAX)**, which generates **9.63%** of the total fare.

---

### Seasonal Trends – Chicago O'Hare International-Philadelphia International Route
Visual Representation of Monthly Flight Trends for ORD-PHL


  * **Peak Months:** August (**1,025 flights**) and July (**1,013 flights**), indicating high summer travel demand.
  * **Lowest Flights:** February (**608 flights**), suggesting seasonality effects.
  * **Annual Average:** The trend follows typical airline seasonality, with **demand peaking** during **summer** and **declining in winter months.**
