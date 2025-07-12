# 🌐 RedeemX REST API

The **RedeemXRestAPI**  provides a RESTful interface to the [RedeemCodeX](https://builtbybit.com/resources/redeemcodex.68885) plugin. It allows **external systems** to manage, codes or templates via HTTP requests.

---

## ⚙️ Configuration

* Install the Latest version of [RedeemXRestAPI](https://github.com/ItzYashvardhan/RedeemXRestAPI/tags)
* Setup the API `host` and `port` inside `config.yml`. Generally default `localhost` used
* All requests must include a valid token using the `Authorization` header.

---

## 🔐 Authentication

All endpoints require an `Authorization` **Header**:

```yaml
Authorization: token #Generated in config.yml
```

---

## 📦 Endpoints

!!!abstract "Base Url"
     ```/api/rcx/{endpoint}```

### `/generate/code`

Generates redeem codes either randomly or from custom input.

**Body Parameters:**

| Parameter  | Type   | Required | Description                                                |
| ---------- | ------ | -------- | ---------------------------------------------------------- |
| `digit`    | Int    | No      | Number of random codes to generate                         |
| `custom`   | String | No       | Space-separated custom codes                               |
| `amount`   | Int    | No       | Times each code can be redeemed (default: `1`)             |
| `template` | String | No       | Template name to associate codes with (default: `DEFAULT`) |

!!!note
    You should provide at least `digit` or `custom` or both.

!!!example "Example Request"
    ```json
        {
        "digit": 2,
        "amount": 5,
        "template": "VIP"
        }
    ```

---

### `/generate/template`

Creates a new code template.

**Body Parameters:**

| Parameter  | Type   | Required | Description              |
| ---------- | ------ | -------- | ------------------------ |
| `template` | String | Yes      | Name of the new template |

!!!example "Example Request"
    ```json
        {
        "template": "SUMMER2025"
        }
    ```

---

### `/delete/code`

Deletes specific codes or all codes under given templates.


**Body Parameters:**

| Parameter  | Type   | Required | Description                             |
| ---------- | ------ | -------- | --------------------------------------- |
| `code`     | String | No       | Space-separated list of codes to delete |
| `template` | String | No       | Delete all codes under these templates  |

!!!example "Example Request"
    ```json
        {
        "code": "VIPACCESS1 VIPACCESS2"
        }
    ```

!!!note
    You should provide at least `code` or `template` or both.

---

### `/delete/template`

Deletes entire templates and all their codes.


**Body Parameters:**

| Parameter  | Type   | Required | Description                          |
| ---------- | ------ | -------- | ------------------------------------ |
| `template` | String | Yes      | Name(s) of the template(s) to delete |

!!!example "Example Request"
    ```json
        {
        "template": "SUMMER2025"
        }
    ```
