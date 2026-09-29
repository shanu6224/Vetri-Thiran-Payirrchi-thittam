# Functional Requirements

| ID | Requirement |
|---|---|
| FR-01 | Create `u_institution_details` table. |
| FR-02 | Store student, faculty, branch and contact details. |
| FR-03 | Support ECE, EEE and CSE branch values. |
| FR-04 | `bb1` users can read EEE records. |
| FR-05 | Users without the required read access cannot read records. |
| FR-06 | Administrators retain access. |
| FR-07 | `bb2` controls create access. |
| FR-08 | `bb3` controls write access. |
| FR-09 | `bb4` controls delete access. |
| FR-10 | Validate behavior through impersonation. |

## Non-functional requirements

- Use least-privilege roles.
- Keep ACL scripts readable and auditable.
- Test positive and negative access cases.
- Keep ServiceNow evidence separate from source documentation.
