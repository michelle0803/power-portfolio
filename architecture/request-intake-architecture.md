# Request Intake & Approval Platform — Architecture

```mermaid
flowchart LR
  U[Users] --> PA[Power Apps Canvas];
  PA --> DV[(Dataverse)];
  DV --> FA[Power Automate Approval Flow - Single Approver];
  FA --> N[Notifications - Email/Teams];
  DV --> PBI[Power BI Dashboard - Backlog Trends and Executive Reporting];