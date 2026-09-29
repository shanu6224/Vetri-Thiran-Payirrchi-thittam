# Test Cases

| TC | User/roles | Action | Expected |
|---|---|---|---|
| TC01 | admin | Read ECE/EEE/CSE | All records visible |
| TC02 | bb1 | Read EEE | Allowed |
| TC03 | bb1 | Read ECE | Denied/not visible |
| TC04 | bb1 | Read CSE | Denied/not visible |
| TC05 | no bb1 | Read | Denied |
| TC06 | bb1+bb2 | Create | New button/create permitted |
| TC07 | bb1+bb2+bb3 | Write | Edit permitted according to ACL evaluation |
| TC08 | bb1+bb2+bb3+bb4 | Delete | Delete permitted according to ACL evaluation |
| TC09 | missing bb2 | Create | Denied |
| TC10 | missing bb3 | Write | Denied |
| TC11 | missing bb4 | Delete | Denied |

## Evidence

Add screenshots from the ServiceNow instance to:

`8. Project Demonstration/`

Suggested names:
- `01-admin-all-records.png`
- `02-bb1-eee-records.png`
- `03-unauthorized-user.png`
- `04-create-access.png`
- `05-write-access.png`
- `06-delete-access.png`
