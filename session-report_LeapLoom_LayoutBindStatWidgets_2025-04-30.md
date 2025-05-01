# Session Report - FrogPad - Session 2.2 - Layout and Bind Stat Box Widgets

## Session Title
Layout and Bind Stat Box Widgets on Dashboard Home

## Date
April 30, 2025

## Objective
Place stat box widgets on the Dashboard Home page in Appsmith and bind them to the corresponding queries.

## Steps
1. **Open the Dashboard Home Page in Appsmith**  
   - Navigate to the Dashboard Home page within your Appsmith application.

2. **Add Stat Box for Memory Configs**  
   - Drag a Statbox widget onto the canvas.  
   - Set the **Label** to “Total Memory Configs”.  
   - Bind the **Value** field to `{{ TotalMemoryConfigs.data.total_memory_configs }}`.

3. **Add Stat Box for Proxy Logs**  
   - Drag another Statbox.  
   - Label: “Total Proxy Logs”.  
   - Bind Value: `{{ TotalProxyLogs.data.total_proxy_logs }}`.

4. **Add Stat Box for Recent Sessions**  
   - Add a Statbox widget.  
   - Label: “Recent Sessions (24h)”.  
   - Bind Value: `{{ RecentSessions24h.data.recent_sessions }}`.

5. **Optional: Add Stat Box for Wiring Events**  
   - Drag a Statbox widget.  
   - Label: “Total Wiring Events”.  
   - Bind Value: `{{ TotalWiringEvents.data.total_wiring_events }}`.

6. **Arrange and Style**  
   - Position the stat boxes in a responsive row.  
   - Apply consistent sizing and alignment.  
   - Save the page layout.

## Deliverable
- Dashboard Home page displays four stat boxes with live metric values.

## Duration
Approximately 30 minutes.

## Flow Diagram
```mermaid
flowchart TD
  A[Start Session 2.2] --> B[Open Dashboard Home]
  B --> C[Add Memory Configs Statbox]
  C --> D[Bind to TotalMemoryConfigs Query]
  D --> E[Add Proxy Logs Statbox]
  E --> F[Bind to TotalProxyLogs Query]
  F --> G[Add Recent Sessions Statbox]
  G --> H[Bind to RecentSessions24h Query]
  H --> I[Add Wiring Events Statbox (Optional)]
  I --> J[Bind to TotalWiringEvents Query]
  J --> K[Save and Style Layout]
  K --> L[End Session 2.2]
```

## 🧠 Memory Reset Recovery Note
To resume: verify all Dashboard stat boxes are correctly bound and displaying expected values before moving to the mini-tables.
