# Project Report

## Title
Script-Controlled ACL – Restrict Record Access Based on Field Value

## Objective
Implement record-level access control in ServiceNow using custom roles, a branch data condition and a scripted ACL.

## Technologies
- ServiceNow
- ACL (Access Control List)
- GlideSystem (`gs`) scripting
- User impersonation for verification

## Implementation
A custom `u_institution_details` table stores student information. Four custom roles control the four CRUD operations. The READ ACL uses both the role and Branch condition, while the script explicitly permits administrators and authorized users.

## Result
The project demonstrates how ServiceNow ACL evaluation can combine:
- user roles,
- record conditions,
- server-side scripts,
- and CRUD operations.

## Evidence
See `8. Project Demonstration/`.
