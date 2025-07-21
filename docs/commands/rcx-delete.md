# 🗑️ Delete Command

The `/rcx delete` command allows administrators to delete redeem **codes** or **templates**, either individually or in bulk.

---

## :octicons-code-square-16: Syntax
```
/rcx delete code <code> [codes]
```
```
/rcx delete code * CONFIRM
```
```
/rcx delete template <template> [templates]
```
```
/rcx delete template * CONFIRM
```

| Command                                    | Description                                      |
|--------------------------------------------|--------------------------------------------------|
| `/rcx delete code <code>`                  | Delete a specific redeem code                   |
| `/rcx delete code <code1> <code2> ...`     | Delete multiple codes in one command            |
| `/rcx delete code * CONFIRM`               | Delete all codes (requires confirmation)        |
| `/rcx delete template <template>`          | Delete a specific template                      |
| `/rcx delete template <tpl1> <tpl2> ...`   | Delete multiple templates at once               |
| `/rcx delete template * CONFIRM`           | Delete all templates (requires confirmation)    |

---

## :octicons-terminal-16: Examples

!!! example "Delete a single code"
    ```
    /rcx delete code VIPACCESS
    ```

!!! example "Delete multiple templates"
    ```
    /rcx delete template EVENT2024 SUMMER2025
    ```
!!! example "Delete All templates codes"
    ```
    /rcx delete code * VIP
    ```
!!! danger "Delete Template Incuded All Linked Codes"
    ```
    /rcx delete template PREMIUM
    ```

    ⚠️ Be very careful — this will remove template and its associated redeem codes.
!!! danger "Delete all codes"
    ```
    /rcx delete code * CONFIRM
    ```

    ⚠️ Be very careful — this will permanently remove all codes.

---

## :octicons-shield-check-16: Permissions Required

```yaml
redeemx.admin.delete
```

!!! warning "No undo for deletions"
    Always back up your codes database and templates.yml before performing mass deletions.