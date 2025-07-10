# 🎟️ Redeem Command

The `/redeem` command allows players to claim rewards using special codes. These codes can be generated and customized by admins through the RCX command system or templates.

---

## :octicons-code-square-16: Syntax

```
/redeem <code> [pin]
```


| Argument | Required | Description                           |
|----------|----------|---------------------------------------|
| `<code>` | Yes      | The redeem code to be used            |
| `[pin]`  | No       | Optional PIN (if the code requires it)|

!!!note "" 
    If a code has a PIN set, the `[pin]` must be provided. Otherwise, leave it blank.


!!!example "Example"
    ```
        /redeem VIPACCESS
    ```
    ```
        /redeem SECRET2025 9844
    ```

## :octicons-shield-check-16: Permissions Optional

```yaml
redeemx.use
```