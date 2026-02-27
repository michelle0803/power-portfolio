# GCC High Action Item Tracking — Architecture

```mermaid
flowchart LR
  U[Users] --> PA[Power Apps (Canvas)]
  PA --> SP[(SharePoint Lists)]
  SP --> F1[Power Automate Scheduled Flow<br/>Reminder Logic (7/3/1 Days)]
  F1 --> O[Outlook Email Notifications]
  SP --> R[Operational Views<br/>(Overdue, Assigned, Due Soon)]