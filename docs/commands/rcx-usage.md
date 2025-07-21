# 📊 Usage Command

The `/rcx usage` command displays detailed usage statistics for a **redeem code** or **template**.  
It helps admins track who used a code, when it was used, and how many times it has been redeemed.

---

## :octicons-code-square-16: Syntax

```

/rcx usage code <code>
/rcx usage template <template>

```

| Command                             | Description                                 |
|-------------------------------------|---------------------------------------------|
| `/rcx usage code <code>`            | Show usage details for a specific code      |
| `/rcx usage template <template>`    | Show overall usage data of a template       |

---

## 📋 What It Shows

- Code/Template Enablity
- Player redemption records
- Player limit records
- Messages, Commands, Sounds
- Pin Protection
- Permission
- Sync status with template
- Target Players

!!! tip "Useful for audit and stats"
    Great for reviewing how many players claimed a reward, and how many redemptions are left.

---

## :octicons-terminal-16: Examples

!!! example "Usage for a single code"
    ```
    /rcx usage code EVENT2025
    ```

!!! example "Usage summary for a template"
    ```
    /rcx usage template VIPDROP
    ```

---

## :octicons-shield-check-16: Permissions Required

```yaml
redeemx.admin.usage
```

!!! info "Same as /rcx preview"
    The same permission covers both `/rcx preview` and `/rcx usage`.

---

!!!note "Notes"
    * Usage info is pulled from the plugin’s internal logs
    * Useful for managing bulk codes and ensuring fair distribution
    * Does not show PIN or internal rewards (use `/rcx preview` for that)

!!! warning "Not editable"
    This is **read-only** data. To reset or update code properties, use `/rcx modify`.

