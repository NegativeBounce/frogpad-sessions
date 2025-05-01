# Session Report - FrogPad - Session 2.1 - Dashboard Stat Queries

## Session Title
Create Stat Queries for Dashboard Home Page

## Date
April 30, 2025

## Objective
Define and validate SQL queries in Appsmith to retrieve key dashboard metrics from the FrogPad PostgreSQL database.

## Steps
1. **Create `TotalMemoryConfigs` Query**  
   - SQL:
     ```sql
     SELECT COUNT(*) AS total_memory_configs
       FROM public.memory_configs;
     ```
   - Run and confirm the returned count.

2. **Create `TotalProxyLogs` Query**  
   - SQL:
     ```sql
     SELECT COUNT(*) AS total_proxy_logs
       FROM public.proxy_logs;
     ```
   - Run and confirm the returned count.

3. **Create `RecentSessions24h` Query**  
   - SQL:
     ```sql
     SELECT COUNT(*) AS recent_sessions
       FROM public.session_reports
      WHERE session_date >= now() - INTERVAL '1 day';
     ```
   - Run and ensure it reflects sessions from the last 24 hours.

4. **(Optional) Create `TotalWiringEvents` Query**  
   - SQL:
     ```sql
     SELECT COUNT(*) AS total_wiring_events
       FROM public.wiring_log;
     ```
   - Run and confirm the count.

## Deliverable
- Four Appsmith queries returning correct metric values for Dashboard home.

## Duration
Approximately 45 minutes.

## Flow Diagram
```mermaid
flowchart TD
  A[Start Session 2.1] --> B[Create TotalMemoryConfigs Query]
  B --> C[Create TotalProxyLogs Query]
  C --> D[Create RecentSessions24h Query]
  D --> E[Create TotalWiringEvents Query (Optional)]
  E --> F[Verify Results]
  F --> G[End Session 2.1]
```

## 🧠 Memory Reset Recovery Note
To resume: ensure each dashboard query exists in Appsmith and returns the expected metric.
