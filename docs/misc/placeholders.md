
# 🧩 Placeholders

RedeemCodeX supports a wide range of dynamic placeholders that can be used in messages, titles, sounds, GUIs, and more.  

---

## 🧷 How to Use

You can use placeholders in:

- Reward messages
- Titles and subtitles
- commands
- Action bars
- GUI
- Sounds
- Logs

---

## 📑 Internal Placeholder List

!!!note "Discription"
    These placeholder can only use within the rcx commands

| Placeholder                          | Description                                      |
|--------------------------------------|--------------------------------------------------|
| `player`                             | Name of the player using the code                |
| `args`                               | Arguments passed with the command                |
| `property`                           | Current modified property                        |
| `code`                               | The code being redeemed                          |
| `total_code`                         | Total number of codes                            |
| `status`                             | Current status of the code (enabled/disabled)    |
| `sync_property`                      | Property being synced from template              |
| `sync_value`                         | Sync value (true/false)                          |
| `renewed_player`                     | Name of the player who renewed the code          |
| `cooldown`                           | Overall cooldown value                           |
| `command_cooldown`                   | Cooldown for the current command                 |
| `code_cooldown`                      | Cooldown of the code                             |
| `duration`                           | Remaining duration of the code                   |
| `expiry`                             | Expiration timestamp                             |
| `expired`                            | Whether the code is expired (true/false)         |
| `total_redemption`                   | Total number of times the code was redeemed      |
| `player_redeemed`                    | Total number of players who used the code        |
| `max_player_limit`                   | Maximum players allowed to redeem the code       |
| `max_redemption`                     | Maximum redemption count allowed                 |
| `permission`                         | Permission required to use the code              |
| `pin`                                | PIN required for the code                        |
| `command`                            | Current command in execution                     |
| `id`                                 | ID of the command                                |
| `target`                             | Target player(s) for the code                    |
| `usedBy`                             | Name of the player using the code                |
| `redeemed_by`                        | Player who redeemed the code                     |
| `template`                           | Template name the code is based on               |
| `sync`                               | Whether the code is synced with template         |
| `min`                                | Minimum length for code generation               |
| `max`                                | Maximum length for code generation               |
| `digit`                              | Number of digits for generated code              |
| `reward_message`                     | Message shown in chat upon redeem                |
| `reward_message_id`                  | Message ID (used in GUI or system)               |
| `reward_actionbar`                   | Actionbar message                                |
| `reward_title`                       | Title displayed                                  |
| `reward_subtitle`                    | Subtitle displayed                               |
| `reward_fade_in`                     | Title fade-in time                               |
| `reward_stay`                        | Title stay time                                  |
| `reward_fade_out`                    | Title fade-out time                              |
| `sound`                              | Sound played on redeem                           |
| `sound_volume`                       | Volume of the sound                              |
| `sound_pitch`                        | Pitch of the sound                               |
| `current_version`                    | Current version of the plugin                    |
| `author`                             | Plugin author                                    |

---

## 🔳 External Placeholders

!!!note "Discription"
    These placeholder can be use with the any command that supprot PlaceHolderApi.

| Placeholder                          | Description                                            |
|--------------------------------------|--------------------------------------------------------|
| `%redeemx_total_codes%`               | Total number of codes in the system                                        |
| `%redeemx_total_templates%`           | Total number of templates in the system                                    |
| `%redeemx_can_redeem_code_{code}%`    | Whether the player can redeem the given code (returns message like ALLOWED, etc.) |
| `%redeemx_can_redeem_code_bool_{code}%` | Whether the player can redeem the code (true/false)                     |
| `%redeemx_can_redeem_template_{template}%` | Whether the player can redeem a specific template (returns status)    |
| `%redeemx_can_redeem_template_bool_{template}%` | Whether the player can redeem the template (true/false)         |
| **`%redeemx_redemption%`                | Total number of times the player has redeemed any code                     |
| **`%redeemx_unique_redemption%`         | Total number of unique codes the player has redeemed                       |
| **`%redeemx_codes%`                     | List of all codes redeemed by the player                                   |
| **`%redeemx_codes_template_{template}%` | List of codes redeemed from a specific template                            |
| **`%redeemx_redemption_template_{template}%` | Number of redemptions from a specific template                         |


!!!abstract "TODO"
    Some of the placeholder which are marked with `*` will not work as it is still being added

## 🧪 Example Usage

!!! example "Using placeholders in messages"
    ```yaml
    &fYou have successfully redeemed {code}!
    ```

!!! example "In reward title"
    ```yaml
    reward_title: "&aCongrats, {player}!"
    ```

---

!!!warning ""

    - Placeholders are case-sensitive.
    - Ensure PlaceholderAPI is installed if using external placeholders .
    - Built-in placeholders work even without PlaceholderAPI for internal plugin features.


---



