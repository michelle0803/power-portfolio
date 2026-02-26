# Enterprise Request Intake & Approval Platform  
**Power Apps + Dataverse + Power Automate + Power BI**

## Overview

Designed and delivered a centralized request intake and approval platform within a commercial Microsoft 365 tenant using Power Apps, Dataverse, Power Automate, and Power BI.

The solution replaced email-based submissions with a structured, secure, and performance-optimized system that improved approval visibility, reduced processing friction, and enabled executive-level operational reporting.

---

## Business Problem

The organization relied on email and spreadsheet tracking to manage operational requests. This created:

- Inconsistent data capture
- Lost or delayed submissions
- Manual follow-ups for status updates
- No centralized visibility into backlog trends
- Limited insight for leadership into request volume and processing times

Leadership lacked reliable data to assess throughput, bottlenecks, or performance trends.

---

## Environment Context

- Commercial Microsoft 365 tenant
- Enterprise user base across multiple departments
- Role-based data visibility requirements
- Moderate-to-high request volume requiring performance optimization
- Structured Dev → Test → Prod deployment model

---

## Architecture

![Architecture Diagram](../architecture/request-intake-architecture.png)

### Technology Stack

- **Frontend:** Power Apps (Canvas App)
- **Data Layer:** Dataverse (custom relational tables)
- **Automation:** Power Automate (approval workflow + notifications)
- **Reporting:** Power BI (operational + executive dashboards)

---

## Data Model Design (Dataverse)

Implemented a normalized data model to ensure scalability and reporting flexibility:

- Requests (primary table)
- Request Categories
- Status History
- SLA Tracking fields
- Approval Metadata

Key design considerations:

- Indexed frequently queried columns to support delegation-safe filtering
- Structured choice fields for reporting consistency
- Separation of display logic from stored data values
- Designed with reporting schema alignment in mind

Dataverse was selected over SharePoint to support:

- Structured relational data
- Scalable security model
- Reliable reporting integration
- Long-term extensibility

---

## Power App Engineering

The Canvas app was engineered with performance and maintainability in mind.

### Performance Optimizations

- Delegation-safe filtering using indexed columns
- Reduced unnecessary OnStart data loads
- Conditional data loading based on user role
- Optimized gallery rendering with filtered datasets
- Controlled variable scope to minimize recalculation overhead

The UI was designed to:

- Adapt dynamically to request status
- Provide clear visual indicators for pending vs approved items
- Minimize clicks for approvers
- Reduce submission errors through structured validation logic

---

## Approval Workflow Design

The workflow included:

- Single-stage approval routing
- Automated email and Teams notifications
- Status updates written back to Dataverse
- SLA timestamp tracking
- Failure notification and retry handling

Flow design emphasized:

- Clear separation between approval logic and notification logic
- Structured error handling with administrative alerts
- Maintainable flow structure to support future expansion

---

## Reporting & Executive Visibility

Developed a Power BI dashboard connected directly to Dataverse to provide:

### Operational Metrics
- Open vs closed requests
- Average approval time
- Aging backlog analysis
- Volume trends by request category

### Executive Reporting
- Monthly submission trends
- Throughput analysis
- SLA performance tracking
- Department-level workload distribution

This enabled leadership to identify bottlenecks and proactively allocate resources.

---

## Key Engineering Decisions

**Why Dataverse?**  
To support structured relational data, scalable security roles, and seamless Power BI integration.

**Why Canvas App?**  
To allow precise UX control and optimized performance tuning.

**Why performance-first design?**  
Enterprise adoption depends heavily on responsiveness and reliability.

---

## Results

- Reduced manual tracking effort significantly
- Improved visibility into request backlog trends
- Enabled executive-level operational insights
- Increased data consistency and reporting accuracy
- Improved overall approval transparency

---

## Lessons Learned

- Designing the reporting model early prevents downstream rework
- Indexing strategy directly impacts gallery performance
- Clear SLA definitions must precede workflow automation
- UX simplicity drives user adoption more than feature density

---

## Future Enhancements

- Expand approval routing logic to support multi-stage scenarios
- Introduce predictive backlog analytics
- Add workload forecasting dashboards
- Integrate AI-assisted request categorization

---

## Competencies Demonstrated

- Enterprise Power Platform Architecture
- Dataverse Data Modeling
- Canvas App Performance Optimization
- Power Automate Workflow Design
- Executive Reporting with Power BI
- ALM Discipline (Dev → Test → Prod)
- Structured Governance in Commercial Tenant
