# Request Intake & Approval Platform — Architecture

```mermaid
flowchart LR
  U[Users] --> PA[Power Apps (Canvas)]
  PA --> DV[(Dataverse)]
  DV --> FA[Power Automate<br/>Approval Flow (Single Approver)]
  FA --> N[Notifications<br/>(Email/Teams)]
  DV --> PBI[Power BI Dashboard<br/>(Backlog Trends, Exec Reporting)]