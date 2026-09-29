# Project Idea

## Title
Script-Controlled ACL – Restrict Record Access Based on Field Value

## Problem
Institution Details contains student information that should not be visible to every user. Access must depend on both the user's role and the record's Branch value.

## Proposed solution
Use ServiceNow record ACLs with custom roles and a scripted READ ACL. The READ ACL combines:
1. a role requirement (`bb1`),
2. a data condition (`Branch is EEE`),
3. a script that permits administrators and authorized users.

## Expected result
EEE users can access EEE records while unauthorized users cannot read the table.
