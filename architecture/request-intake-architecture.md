# Request Intake & Approval Platform — Architecture

flowchart LR
  U[Users] --> PA[Power Apps (Canvas)]
  PA --> DV[(Dataverse)]
  DV --> FA[Power Automate Flow<br/>Single Approver]
  FA --> N[Notifications<br/>(Email/Teams)]
  DV --> PBI[Power BI Dashboard<br/>(Backlog Trends, Exec Reporting)]