# High-Volume Contact Center Demand & Erlang C Workforce Capacity Model

End-to-end Python workforce capacity and queuing model analyzing **50,000+ live service requests** from the NYC 311 Open Data API to optimize 24x7 shift staffing, protect **80/20 Service Level Agreements (SLAs)**, and quantify the headcount ROI of **AI self-service deflection**.

## 1. Executive Summary & Operational Problem
High-volume service operations face severe intraday arrival volatility where simple workload averages (`Calls × AHT / 3600`) understaff peak intervals and cause queue meltdowns. Using 50,000 production arrivals across digital and voice channels, this model:
1. Audits omnichannel intake mix (`ONLINE`, `MOBILE`, `PHONE`) and isolates the top call drivers hitting synchronous voice agents.
2. Engineers a 24-hour intraday arrival profile comparing **Average Daily Demand** vs. **Peak Surge Demand**.
3. Runs an automated **Erlang C Poisson Queuing Solver** across all 24 hours (`300s` AHT, `25%` shrinkage, `80%` answered within `20s`) to output exact hourly FTE schedules and quantify how **25% AI Voice Triage Deflection** absorbs peak demand surges without adding headcount.

## 2. Key Operational Findings (50,000 Live Service Requests)
* **Channel Mix:** While `ONLINE` (**55.8%**) and `MOBILE` (**19.0%**) handle ~75% of total volume, **`PHONE` still accounts for 19.4% (`9,688` synchronous voice calls)** requiring real-time agent staffing.
* **Pareto Call Driver Concentration:** A single seasonal outage category (**`HEAT/HOT WATER` — `3,054` calls**) drives **31.5%** of the entire live voice queue, followed by routine reporting categories (`Noise - Residential` at **7.7%**, `Illegal Parking` at **5.0%**, `Blocked Driveway` at **3.5%**).
* **Intraday Surge & The 11 PM Anomaly:** Voice arrivals trough at **3:00 AM (`45.5` avg calls/hr)**, surge more than **3.5x to a 10:00 AM peak (`168` avg / `232` peak calls/hr)**, and exhibit a secondary late-night spike at **11:00 PM (`110.6` avg / `127.0` peak calls/hr)**.
* **Erlang C Staffing & AI Deflection ROI:** Achieving an 80/20 SLA during the 10:00 AM peak surge requires **`32.0` scheduled FTEs** (at 25% shrinkage). Deflecting just **25%** of peak voice traffic via an automated AI triage agent reduces peak staffing requirements right back down to baseline shift capacity—saving **`7.3+` peak FTEs** while protecting the 80/20 SLA.

## 3. Repository Contents
* **`nyc_311_erlang_c_capacity_model.ipynb`** — Complete Python pipeline (`pandas`, `numpy`, `math`) covering live Socrata API ingestion, timestamp engineering, channel & Pareto driver analysis, automated Erlang C SLA solver, and 24-hour shift visualizations.
