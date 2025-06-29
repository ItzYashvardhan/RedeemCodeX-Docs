# 🛠️ Modify Command

The `/rcx modify` command allows administrators to change various properties of redeem codes and templates. This includes limits, permissions, rewards, messages, duration, sounds, and more — either directly or via GUI i.e. Rewards.

---

## :octicons-code-square-16: Syntax

=== "Code"
    ```
    /rcx modify code <code> <property> [values]
    ```
=== "Template"
    ```
    /rcx modify template <template> <property> [values] 
    ```

---
## 🧰 Modify Properties
List of all available properites with desciption.


### 🔄 `enabled`

=== "Code"
    Enable or disable certain code.
    ```
    /rcx modify code <code> enabled
    ```

=== "Template"
    Enable or disable certain template code.
    ```
    /rcx modify template <template> enabled
    ```

---

### 🔢 `redemption`


=== "Code"
    Set max number of redemptions for code (total usage limit).
    ```
    /rcx modify code <code> redemption <value>
    ```

=== "Template"
    Set max number of redemptions for template (total usage limit).
    ```
    /rcx modify template <template> redemption <value>
    ```
`value` must be a integer type.

!!!info ""
    Set the value **`-1`** to disable the restriction


---

### 👥 `limit`

Set how many unique players can redeem this code.

=== "Code"
    ```
    /rcx modify code <code> limit <value>
    ```

=== "Template"
    ```
    /rcx modify template <template> limit <value>
    ```

`value` must be a integer type.

!!!info ""
    Set the value **`-1`** to disable the restriction

---

### 🔐 `permission`

=== "Code"
    Toggle the permission enablity for code
    ```
    /rcx modify code <code> permission
    ```
    Set custom permission for code
    ```
    /rcx modify code <code> permission <value>
    ```

=== "Template"
    Toggle whether the template requires permission for redemption. If enabled, any code generated from this template will automatically inherit that permission requirement.
    ```
    /rcx modify template <template> permissionRequired
    ```
    Set custom permission for template
    ```
    /rcx modify template <template> permission <value>
    ```
`value must be a string type`
!!!info
     When modifying the permission property for a code or template, if no value is provided, the default permission will be automatically taken from the template.yml.
---

### 🔑 `pin`

Set or change the PIN required for redemption.

=== "Code"
    ```
    /rcx modify code <code> pin <value>
    ```

=== "Template"
    ```
    /rcx modify template <template> pin <value>
    ```

`value` must be a integer type.

!!!info ""
    Set the value **`-1`** to disable the pin

!!! tip
    PINs add an extra security layer — useful for limited or exclusive codes.

---

### 🎯 `target`

Control who can redeem a code using player targeting.

    /rcx modify code <code> addTarget <players>
    /rcx modify code <code> removeTarget <players>
    /rcx modify code <code> setTarget <players>
* `addTarget` – Add one or more players to the target list of the code
* `removeTarget` – Remove specific players from the code's target list
* `setTarget` – Replace the existing target list with new players for the code


---

### ⏳ `duration`

Set how long a code stays valid.

=== "Code"
    ```
    /rcx modify code <code> addDuration <value>
    ```
    ```
    /rcx modify code <code> removeDuration <value>
    ```
    ```
    /rcx modify code <code> setDuration <value>
    ```

=== "Template"
    ```
    /rcx modify template <template> addDuration <value>
    ```
    ```
    /rcx modify template <template> removeDuration <value>
    ```
    ```
    /rcx modify template <template> setDuration <value>
    ```

 `Valid Value`- `1d`, `5h`, `30mo`, `15s`,`30m1h`,`3y10mo` etc

---

### 🔁 `cooldown`

Set cooldown duration between redemptions.

=== "Code"
    ```
    /rcx modify code <code> cooldown <value>
    ```

=== "Template"
    ```
    /rcx modify template <template> cooldown <value>
    ```

`Valid Value`- `1d`, `5h`, `30mo`, `15s`,`30m1h`,`3y10mo` etc

---

Great! Here's a revised and improved version of the **`commands` section**, now including support for command prefixes (`-c`, `-p`, `-op`) and real examples using `!!! example` blocks — all neatly styled and aligned with your documentation format:

---

### 🧾 `commands`

Manage the **commands that are executed** when a code or template is redeemed.

Commands can be:

* Run by **console** using `-c` or `-console`
* Run by **player with sudo** using `-p` or `-sudo`
* Run by **player with temporary OP** using `-op`

---

🧠 Prefix Reference

| Prefix | Description                                |
| ------ | ------------------------------------------ |
| `-c`   | Console executes the command (default)               |
| `-p`   | Player executes the command with normal permissions|
| `-op`  | Player executes the command with as a OP|

---

🛠️ Syntax

=== "Code"

    ```
    /rcx modify code <code> addCommand [prefix] <command>
    /rcx modify code <code> removeCommand <id>
    /rcx modify code <code> setCommand <id> [prefix] <command>
    ```
=== "Template"

    ```
    /rcx modify template <template> addCommand [prefix] <command>
    /rcx modify template <template> removeCommand <id>
    /rcx modify template <template> setCommand <id> [prefix] <command>
    ```

!!! note
    Each command is stored in a list and indexed (`0`, `1`, `2`, ...), so you can modify or remove them using their index.

:octicons-terminal-16: Examples

!!! example "Add a sudo player command"
     `/rcx modify code VIP2025 addCommand -p msg %player% Thanks for redeeming!`

!!! example "Add a command with OP"
    `/rcx modify code VIP2025 addCommand -op warp vip`

!!! example "Set a command at index 1"
    `/rcx modify code VIP2025 setCommand 1 -c eco give {player} 1000 `

!!!tip "Tips"
    * `{player}` will be replaced with the player's name during execution.
    * Use `/rcx preview` to test command execution safely.


---
### 🧬 `template`

Assign or update the template of a code is linked to.
    ```
    /rcx modify code <code> template <template>
    ```

---

### 🔄 `sync`
=== "Code"
    Toggle template sync on or off. When enabled, any changes made to the template will automatically apply to the code.
    ```
    /rcx modify code <code> sync
    ```
    !!! warning
        Disabling sync breaks connection with the template — future template changes won’t affect the code.

=== "Template"
    Manually sync all redeem codes. Useful after making changes directly in template.yml.
    ```
    /rcx modify template <template> sync
    ```
    Toggle the sync state of a specific property.

    ```
    /rcx modify template <template> sync redemption
    ```
    ```
    /rcx modify template <template> sync limit
    ```
    ```
    /rcx modify template <template> sync permission
    ```
    ```
    /rcx modify template <template> sync pin
    ```
    ```
    /rcx modify template <template> sync duration
    ```
    ```
    /rcx modify template <template> sync cooldown
    ```
    ```
    /rcx modify template <template> sync commands
    ```
    ```
    /rcx modify template <template> sync rewards
    ```
    ```
    /rcx modify template <template> sync sounds
    ```
    ```
    /rcx modify template <template> sync messages
    ```
    ```
    /rcx modify template <template> sync syncLockedStatus
    ```

    If `disabled`, the code will stop inheriting that property from the template and can be edited independently.
    If `enabled`, the code will inherit the property from the template and cannot be modified separately.



---

### 🖼️ `rewards`

Opens GUI to visually edit rewards.

=== "Code"
    ```
    /rcx modify code <code> rewards
    ```

=== "Template"
    ```
    /rcx modify template <template> rewards
    ```

---

### 🔊 `sounds`

Opens GUI to visually edit rewards.

=== "Code"
    ```
    /rcx modify code <code> sound <sound> [pitch] [volume]
    ```

=== "Template"
    ```
    /rcx modify template <template> sound <sound> [pitch] [volume]
    ```
!!!note "Default Values"
    - pitch: `1.0`
    - voulume: `1.0`
    - Range can be from `0` to `2.0`

---

### 💬 `messages`

Customize custom message for cetain code or template code.

=== "Code"
    ```
    /rcx modify code <code> addMessage <message>
    ```
    ```
    /rcx modify code <code> removeMessage <message-id>
    ```
    ```
    /rcx modify code <code> setMessage <message-id> <message>
    ```

=== "Template"
    ```
    /rcx modify template <template> addMessage <message>
    ```
    ```
    /rcx modify template <template> removeMessage <message-id>
    ```
    ```
    /rcx modify template <template> setMessage <message-d> <message>
    ```

---

### 📢 `title`

Customize custom title & subtitle for cetain code or template code.

=== "Code"
    ```
    /rcx modify code <code> title [fade-in] [stay] [fade-out] <title>
    ```
    >Alternatively 
    ```
    /rcx modify code <code> title <title>
    ```

=== "Template"
    ```
    /rcx modify template <template> title [fade-in] [stay] [fade-out] <title>
    ```
    > Alternatively    
    ```
    /rcx modify template <template> title <title>
    ```
!!!Note "Deafault Values"
    - fade-in: 20 &nbsp;&nbsp;&nbsp; `//In ticks`
    - stay: 70
    - fade-out: 20

---

### 📢 `subtitle`

Customize custom title & subtitle for cetain code or template code.

=== "Code"
    ```
    /rcx modify code <code> subtitle <title>
    ```

=== "Template"
    ```
    /rcx modify template <template> subtitle <title>
    ```


---

## :octicons-shield-check-16: Permissions Required

```yaml
redeemx.admin.use.modify
```

---

!!!tip
    * Use [`/rcx preview`](./rcx-preview.md) to check modified results.


!!! tip "Bulk Modifications Coming Soon"
    Soon you'll be able to modify multiple codes in one command like:
    ```
    /rcx modify code CODE1 playerLimit 10 CODE2 CODE3
    ```


