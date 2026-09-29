# System Design

## Logical flow

```text
User
  |
  v
ServiceNow ACL engine
  |
  +--> Role check
  |
  +--> Data condition: Branch = EEE
  |
  +--> Script evaluation
  |
  v
Allow / Deny
```

## ACL matrix

| Operation | Role | Branch condition in supplied lab |
|---|---|---|
| Read | bb1 | EEE only |
| Create | bb2 | None |
| Write | bb3 | None |
| Delete | bb4 | None |
| Admin read | admin | Script bypass |

## Data model

```text
u_institution_details
├── number / Student Roll Number
├── Student Name -> sys_user
├── Faculty Name -> sys_user
├── Branch -> choice
├── Email
├── Phone Number
└── Description
```
