# 📘 RedeemX Template API

This guide explains how to use the `RedeemTemplateServiceAPI` to manage templates in RedeemCodeX.

---

## 📄 Overview

Templates in RedeemCodeX define reusable settings for generating redeem codes.

Access the template API via:

!!! example
    ```kotlin
        val templateService = RedeemXAPI.template
    ```
---

## 🆕 Creating a Template

To create a new template (or update if it exists):

!!! example
    ```kotlin
        val template = templateService.generateTemplate("VIP")
    ```

You can then modify its properties and upsert it.

---

## ✏️ Modifying a Template

Like codes, templates are just data classes. You can directly modify their fields:

!!! example
    ```kotlin
        template.duration = "3d"
        template.cooldown = "1h"
        template.permission = "event.redeem"
    ```

After modification, remember to save it:

!!! example
    ```kotlin
        templateService.upsertTemplate(template)
    ```

!!! tip
    Upserting ensures the template is saved in the `template.yml`.

---

## 🗑️ Deleting a Template

To delete a template:

!!! example
    ```kotlin
        val success = templateService.deleteTemplate("VIP")
    ```

!!! warning
    If the template is in use by codes, deleting it may affect them.

---

## 📦 Getting Placeholders

To get a placeholder object from a template:

!!! example
    ```kotlin
        val placeholders = templateService.getRCXPlaceHolder(template)
    ```

Useful for GUI or Discord messages.

---

## 📚 Fetching Templates

### 🔹 Get One Template

!!! example
    ```kotlin
        val template = templateService.getTemplate("VIP")
    ```

### 🔹 Get All Template Names

!!! example
    ```kotlin
        val names = templateService.getTemplates()
    ```

---

## 🛠 Full Example

!!! example "Creating and Saving a Template"
    ```kotlin
        val template = templateService.generateTemplate("VIP")
        template.redemption = 3
        template.cooldown = "5m"
        template.commands += listOf("say Welcome VIP")
        templateService.upsertTemplate(template)
    ```

---

## ✅ Recommendation

!!! abstract "Recommended"
    - Define templates for all common code types (e.g., VIP).
    - Always use `upsertTemplate` after modifications.
    - Avoid deleting templates that are actively referenced by codes.
