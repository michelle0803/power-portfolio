# Gallery Performance Patterns (Power Apps)

## Goal

Keep galleries fast and responsive in enterprise apps by reducing:
- Non-delegable queries
- Over-fetching data
- Expensive per-row computations
- Unnecessary re-evaluations

---

## Pattern 1 — Load Data On Demand (not all in OnStart)

Avoid loading large lists during `OnStart`. Instead, load only when needed.


// OnVisible of screen
Set(varLoading, true);
Set(varFilterStatus, "Open");
Set(varLoading, false);

---

## Pattern 2 - Avoid Over-Filtering Chains

Long && chains and nested If() can reduce delegability. Keep the server-side filter minimal:

With(
    {
        _me: Lower(User().Email),
        _status: ddStatus.Selected.Value
    },
    Filter(
        ActionItems,
        AssignedTo.Email = _me &&
        Status.Value = _status
    )
)

## Practical Checklist

- Index SharePoint columns used in filters and sort

- Avoid multi-select columns for large datasets

- Prefer delegable functions

- Don’t preload large datasets on app load

- Keep per-row formulas minimal