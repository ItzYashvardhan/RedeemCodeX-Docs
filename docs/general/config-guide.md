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
  prevent-alt-account: true
```

- **`cooldown`**  
  Adds a cooldown period between each code redemption attempt.

- **`prevent-alt-account`**  
  Once a code is redeemed by a player, it cannot be redeemed again from any alternate account associated with the same IP.

---

## 🧹 Auto Deletion

```yaml
auto-delete:
  expired-codes: true
  redeemed-codes: true
```

| Option           | Behavior                                                    |
| ---------------- | ----------------------------------------------------------- |
| `expired-codes`  | Delete codes after expiration                               |
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
| `equip-armor` | Auto-equip armor when received                |

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
  redeem: true      # Logs the player, code, and redemption time.
  generate: true    # Logs the code and template with creation time. Recommended for bulk generation.
  modify: true      # Logs the code and template with last modification time.
  delete: true      # Logs the code and template with deletion time.
  preview: true     # Logs the code and template when previewed.
  renew: true       # Logs the code and template when renewed.

  webhook:
    enabled: false   # Enable or disable webhook logging.
    
    # Webhook URLs for sending logs to Discord
    url:
      default: YOUR_DISCORD_WEBHOOK_URL
      redeem: YOUR_DISCORD_WEBHOOK_URL
      generate: YOUR_DISCORD_WEBHOOK_URL
      modify: YOUR_DISCORD_WEBHOOK_URL
      delete: YOUR_DISCORD_WEBHOOK_URL
      preview: YOUR_DISCORD_WEBHOOK_URL
      renew: YOUR_DISCORD_WEBHOOK_URL

    # Whether to send only embed messages for each type
    only-embed:
      default: false
      redeem: false
      generate: false
      delete: false
      preview: false
      renew: false

```
### 🔍 Description

* **Logging Flags**: Toggle which code actions get logged to the console and/or webhook.
* **Webhook Integration**: Send logs directly to specific Discord channels using different URLs per action.
* **Embed Mode**: Set `only-embed` to `true` to skip raw log formatting and send only styled embeds.

!!! note "Webhook URL & Embed Behavior"
    - If both default and generate (or any specific action) are set to the same webhook URL, logs for both will be sent — potentially resulting in duplicate messages.<br>
    - The `only-embed` option applies to **individual actions only**. 
    - The `default` webhook does **not** support `only-embed`.  
    - For embed-only messages, make sure you're using **action-specific URLs** like `generate`, `redeem`, etc.
!!!abstract "Recommended"
    Use separate webhook URLs for each action to avoid confusion or duplication.


!!! note "Performance Note"
    Enabling webhook logging — especially with **bulk code generation** — may cause minor delays due to Discord rate limits and processing overhead.

!!! tip "Customize Log Format"
    You can change the actual message layout in `messages.yml` under the `logger` sections.


---

## 🗃️ Database Settings

```yaml
database:
  server: Default

  type: sqlite

  mysql:
    host: localhost
    port: 3306
    name: redeemx
    username: root
    password: password
    additional-options:
      useSSL: false
      allowPublicKeyRetrieval: true
      autoReconnect: true
      serverTimezone: UTC
      characterEncoding: UTF-8
      useUnicode: true
      rewriteBatchedStatements: true

  maximum-pool-size: 5
  leak-detection-threshold: 0
  connection-timeout: 30000
  idle-timeout: 600000
  max-lifetime: 1800000
  debugging: false
  version: 1.2
```
### 📘 Description

- General

| Key      |Description                                                                                                                                                         |
| -------- |------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `server` | Logical name of the server (e.g., `Survival`, `SkyWars`). Codes are only redeemable on servers with the same name. Use `Default` to allow redemption on any server. |
| `type`   | Database type: `sqlite` (local file) or `mysql` (external server).                                                                                                  |

MySQL Section

| Key                     | Description                                                        |
| ----------------------- | ------------------------------------------------------------------ |
| `host`                  | Database server address. Usually `localhost` or your DB host IP.   |
| `port`                  | MySQL port. Default is `3306`.                                     |
| `name`                  | Name of the database schema to use.                                |
| `username` / `password` | Credentials used to access the database.                           |
| `additional-options`    | Extra JDBC driver options to ensure compatibility and performance. |

Connection Pooling (HikariCP)

| Key                        | Description                                                                                             |
| -------------------------- | ------------------------------------------------------------------------------------------------------- |
| `maximum-pool-size`        | Total max DB connections (in-use + idle). Recommended: 5–20 depending on server uses.                   |
| `leak-detection-threshold` | Logs a warning if a connection isn’t returned within this time (ms). Helps find leaks. `0` disables it. |
| `connection-timeout`       | Max wait time (in ms) to get a DB connection from the pool.                                             |
| `idle-timeout`             | How long idle (unused) connections are kept before being closed.                                        |
| `max-lifetime`             | Max lifetime of any connection, regardless of use. Helps clean up stale connections.                    |
| `debugging`                | If `true`, enables extra debug logs for DB operations (not recommended in production).                  |

Version Control

| Key       | Description                                                                                             |
| --------- | ------------------------------------------------------------------------------------------------------- |
| `version` | Internal database version. **Do not change** unless instructed for manual migration or troubleshooting. |

!!!tip "Important Notes"
    
    **Restart Required**
    
    - Any change in database: config requires a full server restart to apply.

    **Multi-Server Networks**

    - Use unique server: names to isolate code redemptions across different game modes/worlds.
