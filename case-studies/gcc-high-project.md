# GCC High Action Item Tracking Platform

## Overview

Designed and delivered a centralized action item tracking system within a **GCC High tenant** using Power Apps, SharePoint, and Power Automate (standard connectors only).

The solution replaced fragmented spreadsheet and email-based tracking with structured accountability, automated reminder notifications, and improved operational visibility.

---

## Problem

The client needed a reliable way to track action items assigned across teams.

This resulted in:

- Missed deadlines  
- Manual reminder emails sent by coordinators  
- No centralized visibility into overdue items  
- Limited accountability for task ownership  
- Inconsistent follow-through on deliverables  

Leadership lacked a clear view of backlog and ownership trends.

---

## Constraints

- No premium Power Platform licensing allowed  
- Limited connector availability  
- Restrictions on custom connectors and API integrations  
- Strict DLP governance policies  
- Higher network latency  
- No separate Dev / Test / Prod environments  
- Manual ALM processes required  

The architecture had to function entirely within these restrictions.

---

## Architecture

![Architecture Diagram](../architecture/gcc-high-action-item-architecture.png)

### Stack

- **Frontend:** Power Apps (Canvas App)  
- **Data Layer:** SharePoint Lists  
- **Automation:** Power Automate (Standard connectors only)  
- **Notifications:** Outlook (GCC High compliant)  

---

## Solution Design

### Data Model (SharePoint)

Designed simplified SharePoint schema to mitigate delegation and performance issues:

- Indexed frequently filtered columns  
- Avoided unnecessary lookup relationships  
- Minimized use of multi-select Person/Group columns  
- Structured choice fields carefully to reduce filtering conflicts  
- Optimized list structure for performance in high-latency networks  

Special care was taken to address delegation limits when filtering by:

- Assigned Owner  
- Due Date  
- Completion Status  

---

### Canvas App Engineering & Performance Tuning

Performance optimization was critical due to SharePoint delegation limits and GCC High latency.

Key optimizations:

- Delegation-safe filtering wherever possible  
- Reduced OnStart data preloading  
- Limited record retrieval to user-specific scope  
- Controlled gallery refresh behavior  
- Avoided non-delegable formula chains  
- Simplified conditional logic to reduce recalculation overhead  

UI design emphasized:

- Clear overdue indicators  
- Owner-specific filtering  
- Minimal friction for status updates  
- Visual task state differentiation  

---

### Automated Reminder Workflow

Built scheduled reminder automation using standard Power Automate connectors:

- Daily scheduled trigger  
- Conditional checks for incomplete items  
- Automated reminder emails sent:
  - 7 days prior to due date  
  - 3 days prior to due date  
  - 1 day prior to due date  
- Logic to prevent duplicate reminders  
- Structured failure handling and admin notifications  

This eliminated the need for manual reminder emails.

---

### Governance & Deployment Discipline

Operating within GCC High required strict governance alignment:

- No premium connectors or external APIs  
- Adherence to DLP policies  
- Manual change management due to lack of environment separation  
- Version-controlled documentation for updates  
- Controlled deployment scheduling  

Design decisions prioritized compliance stability over feature expansion.

---

## Key Engineering Decisions

**Why SharePoint instead of Dataverse?**  
Licensing constraints prohibited premium data services.

**Why simplified schema design?**  
Reduced delegation conflicts and improved reliability in a high-latency environment.

**Why staggered reminder intervals (7/3/1 days)?**  
Balanced accountability with user fatigue.

**Why avoid complex lookups?**  
GCC High latency magnifies performance costs of non-delegable queries.

---

## Results

- Increased visibility of action item ownership  
- Reduced number of overdue tasks  
- Eliminated manual reminder workflow  
- Improved turnaround time on deliverables  
- Increased accountability across teams  
- Centralized tracking replacing fragmented email chains  

---

## Lessons Learned

- Delegation limits require early architectural planning  
- Simpler schemas outperform complex relational structures in restricted environments  
- Automated nudging significantly improves compliance behavior  
- Governance discipline is critical in GCC High deployments  

---

## Core Competencies Demonstrated

- Power Platform Development in GCC High  
- SharePoint Data Architecture  
- Delegation-Aware Canvas App Engineering  
- Workflow Automation Using Standard Connectors  
- Compliance-Conscious Deployment Practices  
- Performance Optimization in High-Latency Environments  
- Governance & DLP Alignment  
