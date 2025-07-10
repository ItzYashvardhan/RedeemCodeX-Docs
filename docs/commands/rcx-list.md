# 📄 List Command

The `/rcx list` command allows administrators to **view existing codes, templates, or redeemed codes by players**. It supports listing by **template**, **player**, or all available templates.

---

## :octicons-code-square-16: Syntax

```
/rcx list code <template>
/rcx list template
/rcx list player <player>
```

| Subcommand        | Required | Description                                      |
| ----------------- | -------- | ------------------------------------------------ |
| `code <template>` | Yes      | Lists all codes created from a specific template |
| `template`        | No       | Lists all available templates                    |
| `player <player>` | Yes      | Shows codes redeemed by a specific player        |

---

## 🔍 Subcommands & Examples

### :octicons-file-code-16: List Codes by Template

!!!example "Example"
    ```
    /rcx list code DEFAULT
    ```

Shows all generated codes based on the `DEFAULT` template.

---

### :octicons-archive-16: List Available Templates

!!!example "Example"
    ```
    /rcx list template
    ```
    

Displays all available code templates registered in the system.

---

### :octicons-person-16: List Codes Redeemed by a Player

!!!example "Example"
    ```
    /rcx list player ItzJustLime
    ```
    

Lists all codes redeemed by the player `ItzYashvardhan`.

---

## :octicons-shield-check-16: Permissions Optional

```yaml
redeemx.admin.use.list
```

