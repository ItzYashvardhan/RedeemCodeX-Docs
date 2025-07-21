# ⚙️ Generate Command

The `/rcx gen` command is used by administrators to generate **redeem codes** or **templates**. It supports bulk generation, custom naming, and template assignment.

---

## :octicons-code-square-16: Syntax


| Command                                       | Description                                                      |
|-----------------------------------------------|------------------------------------------------------------------|
| `/rcx gen code <CUSTOM> [TEMPLATE]`                      | Generate a code with a custom name                               |
| `/rcx gen code <DIGIT> [TEMPLATE] [AMOUNT]`   | Generate digit-based codes from a template                       |
| `/rcx gen template <template>`                | Create a new template with given name                            |

---

## :octicons-terminal-16: Examples

!!! example "Generate a single custom code"
    ```
    /rcx gen code VIPACCESS
    ```
    `Sample Output` <br>
    `Generated CODE: VIPACCESS FROM DEFAULT TEMPLATE`

!!! example "Generate multiple custom code"
    ```
    /rcx gen code CUSTOM1 VIP CUSTOM2 CUSTOM3
    ```
    `Sample Output` <br>
    `Generated CODE: CUSTOM1 CUSTOM2 CUSTOM3 FROM DEFAULT TEMPLATE`

!!! example "Generate Codes using a template"
    ```
    /rcx gen code 4 VIP 5
    ```
    `Sample Output`
    ```
    Generated CODE: 7AK1 AK78 MK12 RCB9 ANIC FROM VIP TEMPLATE
    ```

!!! example "Create a new template"
    ```
    /rcx gen template PREMIUM
    ```

!!! question "Why aren't all generated codes showing in chat?"
    Minecraft chat has a character limit, so if you generate too many codes at once, not all of them may fit in the chat.
    To view **all generated codes**, please check the `logs` folder of plugin.

---

## :octicons-light-bulb-16: Parameters

- `CUSTOM`: Any custom name like `VIP2025`, `SUMMERPASS`
- `DIGIT`: A number indicating how many random digits should be in the code
- `TEMPLATE`: Name of an existing template to apply pre-defined settings to generated codes
- `AMOUNT`: How many codes to generate (defaults to 1 if not specified)

---

## :octicons-shield-check-16: Permissions Required

```yaml
redeemx.admin.gen
```

