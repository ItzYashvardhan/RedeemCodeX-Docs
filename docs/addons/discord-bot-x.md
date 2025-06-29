# 🤖 Discord Bot Addon — RedeemCodeX

The **Discord Bot Addon** lets server admins manage and interact with RedeemCodeX **directly from Discord using slash commands**.

This is perfect for managing templates, codes, and viewing usage data — all without needing in-game or console access.

---

## 💬 Available Slash Commands

These commands are registered via Discord's slash command system:

![Slash Commands](../images/discord-bot-commands.png)

| Command               | Description                                |
|------------------------|--------------------------------------------|
| `/generate`           | Generate redeem codes based on a template  |
| `/modify template`    | Modify the properties of an existing template |
| `/modify code`        | Edit an existing redeem code               |
| `/delete code`        | Delete a specific code    |
| `/usage template`     | View all usages of a specific template     |

---

## 📦 Features

* ✅ Full control over code and template management
* ✅ Easy and quick access for trusted staff
* ✅ Works without needing the Minecraft server console

---

## 🛠 Integration Requirements

* The bot must be **online and authorized** in your Discord server
* The Minecraft server must be able to communicate with the bot (via API/websocket depending on your setup)
* RedeemCodeX must have API integration enabled
