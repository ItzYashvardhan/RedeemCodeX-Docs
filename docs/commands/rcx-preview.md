# 👁️ Preview Command

The `/rcx preview` command allows administrators to **simulate the redemption** of a code or template. It executes the full functionality of the code — **rewards, messages, sounds, etc. without actually redeeming it**.

---

## :octicons-code-square-16: Syntax

```
/rcx preview code <code>
```
```
/rcx preview template <template>
```


| Command                                       | Description                                                   |
|-----------------------------------------------|---------------------------------------------------------------|
| `/rcx preview code <code>`                    | Preview the code                                 |
| `/rcx preview code <code> commands`           | Execute commands of this code                           |
| `/rcx preview code <code> messages`           | Recieve messages, titles and sounds of this code        |
| `/rcx preview code <code> rewards`            | Claim rewards of this code                              |
| `/rcx preview template <template>`            | Preview the template                        |
| `/rcx preview template <template> commands`   | Execute commands of this template                       |
| `/rcx preview template <template> messages`   | Recieve messages, titles and sounds of this template    |
| `/rcx preview template <template> rewards`    | Claim rewards of this template                          |

!!! tip "Perfect for testing"
    Use this to verify that the rewards and its effects are working correctly without actually redeeming the code.

---

## :octicons-terminal-16: Examples

!!! example "Preview a code"
    ```
    /rcx preview code VIPACCESS
    ```

!!! example "Preview a template rewards"
    ```
    /rcx preview template RANKGIFT rewards
    ```

---

## :octicons-shield-check-16: Permissions Required

```yaml
redeemx.admin.preview
```

---

!!!note "On Preview"
    - Code is not consumed during preview
    - No entries are added to usage logs
    - No cooldown or playerLimit is affected
    - Rewards will still be executed (e.g., items/commands will run!)

!!!success "Recommended"
    * Use this before distributing a code to ensure template or code functions are setup correctly.
    * Especially helpful for verifying bulk-generated or synced codes.


