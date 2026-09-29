# ServiceNow Development Steps

## 1. User

Navigate to:

`User Administration → Users → New`

Create:
- User ID: `EEE User`
- First name: `EEE`
- Last name: `User`
- Email: `eeeuser@gmail.com`

## 2. Roles

Create:
- `bb1`
- `bb2`
- `bb3`
- `bb4`

Assign the required roles to the test user.

## 3. Table

Navigate to:

`System Definition → Tables → New`

Create:
- Label: `Institution Details`
- Name: `u_institution_details`
- Extends: false

## 4. Fields

Create the fields described in `README.md`.

## 5. Sample records

Insert multiple records with:
- ECE
- EEE
- CSE

This gives the ACL tests meaningful positive and negative cases.
