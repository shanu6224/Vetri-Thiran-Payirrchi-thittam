# READ ACL

## Configuration

- Type: `record`
- Operation: `read`
- Name: `u_institution_details`
- Active: `true`
- Advanced: `true`
- Requires role: `bb1`
- Data condition: `Branch is EEE`

## Script

```javascript
(function () {
    // Allow admin users full access
    if (gs.hasRole('admin')) {
        return true;
    }

    // Allow only authorized EEE users to pass the script.
    if (gs.hasRole('bb1')) {
        return true;
    }

    return false;
})();
```

## Expected behavior

Because the ACL has a data condition of `Branch is EEE`, a `bb1` user can read only EEE records. The script separately allows administrators and rejects users who do not have `bb1`.
