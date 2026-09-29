# Security Notes

## What the supplied READ ACL guarantees

The READ ACL has:
- role requirement: `bb1`
- data condition: `Branch is EEE`
- script: administrator bypass plus `bb1` check

Therefore, the intended read behavior is:
- Admin: can read all records.
- `bb1`: can read EEE records.
- No `bb1`: cannot pass the read ACL.

## Important distinction for CREATE / WRITE / DELETE

The supplied lab instructions say that CREATE, WRITE and DELETE ACLs have **no data condition**. A role-only ACL does not, by itself, mean "EEE records only."

For example:
- `bb2` may be able to create a record with ECE/CSE unless another ACL/business rule prevents it.
- `bb3` may be able to write records allowed by the applicable ACL evaluation, not necessarily only EEE.
- `bb4` may be able to delete records allowed by the applicable ACL evaluation, not necessarily only EEE.

If the project requirement is strict branch-level enforcement for every operation, implement branch-aware controls for each operation and test them explicitly.

## Safer design principle

Use the smallest privilege required:
- Read → `bb1` + EEE condition
- Create → `bb2` plus validation that the created record is EEE
- Write → `bb3` plus validation that the target record is EEE
- Delete → `bb4` plus validation that the target record is EEE

The exact implementation should be validated in the target ServiceNow release because ACL evaluation and scripting details are instance/version dependent.
