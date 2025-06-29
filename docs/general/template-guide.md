# 🧱 Default Template Configuration

The `DEFAULT:` section in your `template.yml` acts as the base configuration for all generated codes.  
It controls behavior like cooldowns, permissions, limits, and the powerful **sync-lock system** for template properties.

---

## 📐 Default Values

```yaml
DEFAULT:
  enabled: true
  duration: 0s
  cooldown: 0s
  redemption: 1
  player-limit: 1
  permission:
    required: false
    value: "redeemx.use.premium.{code}"
  pin: 0
  default-sync: false
  commands: []
  messages:
    - "&aThanks for redeeming!"
  sound: ""
  rewards: ""
```

| Key            | Description                                                          |
| -------------- | -------------------------------------------------------------------- |
| `enabled`      | If false, the code will not work until manually enabled              |
| `duration`     | Validity duration (e.g., `1h`, `3d`, `0s` means infinite)            |
| `cooldown`     | Delay between redemptions per player                                 |
| `redemption`   | Max number of redemptions allowed                                    |
| `player-limit` | Max number of unique players who can redeem                          |
| `permission`   | Set whether permission is required and the permission string pattern |
| `pin`          | Optional PIN required to redeem the code                             |
| `default-sync` | Whether this entire template enforces sync on all generated codes    |
| `commands`     | List of commands to run on redeem (empty by default)                 |
| `messages`     | Chat messages shown after redeeming                                  |
| `sound`        | Sound played (e.g., `"ENTITY_PLAYER_LEVELUP"`)                       |
| `rewards`      | Reward definition or reference (GUI-configurable)                    |

---

## 🔄 Sync Lock System

The `sync:` block controls which properties are **locked to the template** and which can be **modified per code**.

```yaml
sync:
  enabled-status: false
  locked-status: false
  target: false
  commands: true
  duration: true
  cooldown: true
  pin: true
  redemption: true
  player-limit: true
  permission: false
  messages: true
  sound: true
  rewards: true
```

### 🔐 Sync Lock Behavior

| Property | Description                                                    |
| -------- | -------------------------------------------------------------- |
| `true`   | Locks the property — cannot be modified via `/rcx modify code` |
| `false`  | Allows modification via `/rcx modify code`                     |

!!! note "Inheritance"
    Even if sync is set to `false`, the code will still **inherit** this value at generation.
    The lock only prevents future modifications, not inheritance.

---

!!!success "Recommended Defaults"
    * 🔒 `commands`, `rewards`, and `messages` — usually should be locked (`true`) to keep consistency.
    * 🔓 `permission`, `pin`, `target` — often useful to leave editable (`false`) for flexibility.
    * 🔒 `cooldown`, `duration`, `redemption` — lock if using time-limited or one-time codes.

---

## 🧪 Example Use Case

!!! example "Prevent editing command list for all codes from this template"
    ```yaml
    sync:
        commands: true
    ```

!!! example "Let staff adjust pin or permission manually"
    ```yaml
    sync:
        pin: false
        permission: false
    ```

---

!!!note "Notes"

    * `{code}` in the permission value will be replaced with the actual code name.
    * The default template (`DEFAULT:`) applies unless explicitly overridden by a custom-named template.

!!!abstract "Future Planned"
    Create named templates in `template.yml` like this:
    ```yaml
    VIPDROP:
        inherits: DEFAULT
        permission:
            required: true
    ```

---
