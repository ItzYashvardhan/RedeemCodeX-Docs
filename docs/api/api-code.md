# 📘 RedeemX Code API

This guide explains how to use the `RedeemCodeServiceAPI` to manage redeem codes in your plugin or addon.

---

## 📄 Overview

The `RedeemCodeServiceAPI` allows for full control of code generation, modification, and synchronization for RedeemCodeX.

Access it via the `RedeemXAPI` object:
!!! example
    ```kotlin
    val codeService = RedeemXAPI.code
    ```
---

## ✅ Creating a Code

### 🔹 Generate by Unique Name
!!! example
    ```kotlin
    val code = codeService.generateCode("WEEKEND_DROP")
    ```

### 🔹 Generate with Digit Count
!!! example
    ```kotlin
    val code = codeService.generateCode(digit = 6)
    ```

### 🔹 Generate Multiple Codes
!!! example
    ```kotlin
    val codes = codeService.generateCode(digit = 8, amount = 5)
    ```

### 🔹 Generate Using Template
!!! example
    ```kotlin
    val code = codeService.generateCode(digit = 5, template = "VIP")
    ```

!!! note
    You can generate codes with or without templates. Templates are optional but useful for categorization.

---

## ✏️ Modifying a Code

Once a code is created, you can edit its fields like any data class:

!!! example
    ```kotlin
        code.redemption = 10
        code.duration = "1h"
        code.cooldown = "10m"
        code.commands.add("give %player% diamond 1")
    ```

!!! warning
    Be sure to re-upload the code using `upsertCode` after making changes, or they will not be saved.

---

## ⬆️ Upsert Code

After modifying the code, save it back to the system using:

!!! example
    ```kotlin
    codeService.upsertCode(code)
    ```

Or for multiple codes:

```kotlin
codeService.upsertCodes(listOf(code1, code2))
```

!!! tip
    Always use `upsertCode` or `upsertCodes` to persist any changes made to a RedeemCode.

---

## 🗑 Deleting Codes

### 🔹 Delete One

```kotlin
codeService.deleteCode("ABC123")
```

### 🔹 Delete Multiple

```kotlin
codeService.deleteCodes(listOf("ABC123", "XYZ456"))
```

### 🔹 Delete All

```kotlin
codeService.deleteAllCode()
```

!!! warning
    `deleteAllCode()` will remove every redeem code in the system. Use with caution.

---

## 📦 Getting Placeholders

To get placeholder values for display:

```kotlin
val placeholders = codeService.getRCXPlaceHolder(code)
```

This returns an `RCXPlaceHolder` object with resolved placeholders for GUI, messages, etc.

!!! example
    Use placeholders to display dynamic code info in your plugin GUIs or Discord bots.

---

## 📚 Fetching Codes

### 🔹 Get One Code

```kotlin
val code = codeService.getCode("ABC123")
```

### 🔹 Get All Code Strings

```kotlin
val codes = codeService.getCodes() // returns Set<String>
```

!!! note
    `getCodes()` returns only the code strings, not the full `RedeemCode` objects.

---

## 🛠 Full Example

!!! example "Full Example of using RedeemXAPI"
    ```kotlin
        //Generate code
        val code = codeService.generateCode(digit = 5)

        //Modify Code
        code.redemption = 10
        code.enabledStatus = true
        code.commands += listOf("say <green>Hello {player}!!</green>") //Mini Message Supported
        
        //Upset Code
        codeService.upsertCode(code) //Important

        //Delete Code
        codeService.deleteCode(code.code)
    ```

## ✅ Recommendation

!!! abstract "Recommended"
    - Always `upsertCode` after modifying to persist changes.
    - Use `template` wisely for categorizing codes.
