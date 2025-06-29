# ⚙️ Configuration Guide

This guide covers all available settings in `config.yml` for RedeemCodeX.  
Each section controls specific behavior like language, code generation limits, command cooldowns, logging, and more.

---

## 🌐 Language Selector

```yaml
lang: "en"
```

!!! note "How to change language?"
    1. Copy the `messages.yml` file and rename it (e.g., `messages_germany.yml`)
    2. Edit the file for your custom language
    3. Set `lang` to your custom file name (without `.yml`):
    `lang: "germany"`

---

## 🔁 Code Generation

```yaml
max-attempts: 1000
```

* Maximum number of retries during bulk code generation to avoid infinite loops.
* Useful if all possible combinations (e.g., all 3-digit codes) are exhausted.

```yaml
code:
  display-amount: 40
  minimum-digit: 3
  maximum-digit: 25
```

| Key              | Description                                       |
| ---------------- | ------------------------------------------------- |
| `display-amount` | Number of codes shown in chat when bulk-generated |
| `minimum-digit`  | Minimum length of generated codes                 |
| `maximum-digit`  | Maximum length of generated codes                 |

---

## 🎟️ Redeem Command

```yaml
redeem-command:
  cooldown: "3s"
  prevent-alt-account: true #TODO
```

* Adds cooldown between redemptions

!!!abstract "Future Planned"
    * Prevents alts (same IP usage) — (Planned/TODO)

<!-- !!! warning "IP Protection"
    Alt-detection checks for the same IP. It won't work if player limits are not set. -->

---

## 🧹 Auto Deletion

```yaml
auto-delete:
  expired-codes: true
  redeemed-codes: true
```

| Option           | Behavior                                                    |
| ---------------- | ----------------------------------------------------------- |
| `expired-codes`  | Delete codes after expiration (on server restart)           |
| `redeemed-codes` | Delete codes when both redemption and player limits are met |

---

## 🎁 Rewards System

```yaml
rewards:
  drop: true
  sound: true
  equip-armor: false
```

| Option        | Description                                   |
| ------------- | --------------------------------------------- |
| `drop`        | Drop item if inventory is full                |
| `sound`       | Play a sound when item is dropped             |
| `equip-armor` | Auto-equip armor when received (planned/TODO) |

---

## 🔄 Code Renewal

```yaml
renew:
  reset-expired: true
  reset-delay: true
  clear-usage: true
  clear-rewards: false
  clear-commands: false
  remove-permission-required: false
```

| Option                       | Description                                            |
| ---------------------------- | ------------------------------------------------------ |
| `reset-expired`              | Renew expired codes using their original duration      |
| `reset-delay`                | Resets all player cooldowns for the code               |
| `clear-usage`                | Resets the player usage list                           |
| `clear-rewards`              | Clears rewards on renew (won’t work if locked)         |
| `clear-commands`             | Clears reward commands on renew (won’t work if locked) |
| `remove-permission-required` | Disables permission requirement if not locked          |

---

## 📜 Logger & Webhook

```yaml
logger:
  generate: true
  modify: true
  delete: true
  redeemed: true
  webhook:
    enabled: false
    url: "YOUR_DISCORD_WEBHOOK_URL"
```

* Controls which actions are logged: code generation, edits, deletions, redemptions.
* Webhook support sends logs to a Discord server.

!!! warning "Webhook Delay"
    Enabling webhook with bulk generation may cause performance delay due to discord integrated system.

---

## 🗃️ Database Settings

```yaml
database:
  version: 1.0
```

!!! danger "Don't change unless required"
    Database versioning is used internally. Modify this only if instructed for upgrades or migration.
