# Script-Controlled ACL – Restrict Record Access Based on Field Value

## Project Summary

This ServiceNow lab implements record-level security using **script-controlled Access Control Lists (ACLs)**.

### Security requirement

- Only users with the custom `bb1` role can read Institution Details records.
- The READ ACL additionally restricts records to `Branch = EEE`.
- Users with `bb2` can create records.
- Users with `bb3` can write/edit records.
- Users with `bb4` can delete records.
- Administrators retain full access through the READ ACL script.
- The project includes setup, ACL configuration, testing, documentation, and demonstration evidence.

> **Important:** The supplied lab specification puts the `Branch = EEE` restriction on the READ ACL only. Therefore, the CREATE/WRITE/DELETE ACLs as specified do not independently enforce the EEE branch. See `7. Project Documentation/SECURITY-NOTES.md` for the distinction and a stricter enforcement option.

## ServiceNow Objects

| Object | Value |
|---|---|
| Custom table label | Institution Details |
| Table name | `u_institution_details` |
| Branch choices | ECE, EEE, CSE |
| Read role | `bb1` |
| Create role | `bb2` |
| Write role | `bb3` |
| Delete role | `bb4` |
| Admin | Full access |

## Table Fields

- Student Roll Number – Auto Number
- Student Name – Reference → User
- Faculty Name – Reference → User
- Branch – Choice: ECE, EEE, CSE
- Email – String
- Phone Number – String
- Description – Multi String

## Read ACL

```javascript
(function () {
    // Allow admin users full access
    if (gs.hasRole('admin')) {
        return true;
    }

    // Allow users with bb1 to read records.
    // The ACL condition separately restricts the record to Branch = EEE.
    if (gs.hasRole('bb1')) {
        return true;
    }

    // Deny all other users.
    return false;
})();
```

### READ ACL configuration

- Type: Record
- Operation: Read
- Name: `u_institution_details`
- Active: true
- Advanced: true
- Requires role: `bb1`
- Data condition: `Branch is EEE`

## Create ACL

- Type: Record
- Operation: Create
- Name: `u_institution_details`
- Active: true
- Requires role: `bb2`
- No data condition, per the supplied lab specification.

## Write ACL

- Type: Record
- Operation: Write
- Name: `u_institution_details`
- Active: true
- Requires role: `bb3`
- No data condition, per the supplied lab specification.

## Delete ACL

- Type: Record
- Operation: Delete
- Name: `u_institution_details`
- Active: true
- Requires role: `bb4`
- No data condition, per the supplied lab specification.

## Role progression

```text
bb1 → Read EEE records
bb1 + bb2 → Read + Create
bb1 + bb2 + bb3 → Read + Create + Write
bb1 + bb2 + bb3 + bb4 → Read + Create + Write + Delete
admin → Full access
```

## Verification URL

After creating the table, the list can be opened using:

```text
u_institution_details.list
```

or by searching for the table in the Application Navigator.

## Repository Structure

```text
Script-Controlled-ACL-ServiceNow-Project/
├── 1. Brainstorming & Ideation/
├── 2. Requirement Analysis/
├── 3. Project Design Phase/
├── 4. Project Planning Phase/
├── 5. Project Development Phase/
├── 6. Project Testing/
├── 7. Project Documentation/
├── 8. Project Demonstration/
├── assets/
└── README.md
```

## Completion checklist

- [ ] Create test user
- [ ] Create roles `bb1`, `bb2`, `bb3`, `bb4`
- [ ] Assign roles to the required test users
- [ ] Create `u_institution_details`
- [ ] Add all required fields
- [ ] Insert ECE, EEE and CSE records
- [ ] Create READ ACL
- [ ] Create CREATE ACL
- [ ] Create WRITE ACL
- [ ] Create DELETE ACL
- [ ] Test impersonation for each role combination
- [ ] Capture ServiceNow evidence screenshots
- [ ] Add evidence to `8. Project Demonstration/`
- [ ] Push the project to GitHub

## GitHub

This repository is documentation/evidence oriented. ServiceNow instance-specific configuration is performed inside the ServiceNow instance; screenshots and exported artifacts can be added to the demonstration folder after testing.
