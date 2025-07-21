# ♻️ Renew Command

The `/rcx renew` command allows administrators to **renew an existing redeem code**, resetting its usage count and player eligibility while retaining its other properties.

---

## :octicons-code-square-16: Syntax

```

/rcx renew <code>

```

| Command               | Description                            |
|-----------------------|----------------------------------------|
| `/rcx renew <code>`   | Reset the redemption state of a code   |

---

## 🔄 What It Does

- Resets the **redemption count**
- Clears the list of **players who have redeemed** the code
- Keeps all other settings (rewards, permission, duration, etc.) unchanged

!!! tip "Perfect for reusing seasonal or event codes"
    You can renew codes like `SUMMER2024` for a new season without creating a new one from scratch.

---

## :octicons-terminal-16: Examples

!!! example "Renew a VIP code"
    ```
    /rcx renew VIPACCESS
    ```

---

## :octicons-shield-check-16: Permissions Required

```yaml
redeemx.admin.renew
```

---

!!!note "Key Points"
    * Renewal **only works on existing codes**, not templates
    * This command is useful for limited-time codes you want to recycle
    * Renewing does **not** change expiration or cooldown — use [`/rcx modify`](rcx-modify.md) for that

!!! warning "Does not affect code configuration"
    Only usage-related data is reset. If you want to change how the code behaves, use [`/rcx modify`](rcx-modify.md).