# Delegation-Safe Filtering Pattern (Power Apps + SharePoint/Dataverse)

## Goal
Keep galleries responsive and avoid non-delegable queries when filtering by:
- Assigned Owner
- Status
- Due Date ranges
- Search text

---

## Pattern: Pre-filter + indexed columns + simplified predicates

### SharePoint (example concepts)
**Recommendations**
- Index columns used in filters: `Status`, `AssignedTo`, `DueDate`
- Avoid complex `in`, multi-select filters, and heavy `AddColumns` on large lists
- Keep the delegable portion in `Filter()` simple and server-friendly

### Example (template)

// Pseudo-pattern: keep the Filter delegable, then apply local shaping if needed
With(
    {
        _status: ddStatus.Selected.Value,
        _user: User().Email
    },
    Filter(
        ActionItems,
        Status.Value = _status &&
        AssignedTo.Email = _user
    )
)

---

## Pattern: Role-aware filtering without loading everything
With(
    {
        _me: Lower(User().Email),
        _isAdmin: varIsAdmin
    },
    If(
        _isAdmin,
        Filter(ActionItems, Status.Value <> "Completed"),
        Filter(ActionItems, AssignedTo.Email = _me && Status.Value <> "Completed")
    )
)

## Performance Tips

- Prefer StartsWith() over Search() for delegable text filtering (where supported)
- Avoid loading multiple lists/tables on OnStart unless truly needed
- Cache small reference tables once; query large tables on-demand
- Multi-person fields and multi-choice fields (SharePoint) can be tricky—test delegation warnings early
- Use pagination patterns (Top N / “Load more”) for very large datasets

## When to use Dataverse instead

If you need:
- Complex relationships and server-side filtering
- Large scale querying without delegation pain
- Row-level security models