# CREATE / WRITE / DELETE ACLs

## CREATE

- Operation: `create`
- Name: `u_institution_details`
- Requires role: `bb2`

## WRITE

- Operation: `write`
- Name: `u_institution_details`
- Requires role: `bb3`

## DELETE

- Operation: `delete`
- Name: `u_institution_details`
- Requires role: `bb4`

These ACLs follow the supplied lab specification and have no data condition.

## Important security note

If the actual business requirement is that **all four operations must be restricted to EEE records**, the CREATE/WRITE/DELETE rules need additional branch-aware logic. See:

`7. Project Documentation/SECURITY-NOTES.md`
