# 🔐 Admin Permissions
!!! tip ""
    These permissions should only be granted to trusted staff members or server administrators.




## 🛠️ Admin Permissions
| Node                       | Description                                           |
| -------------------------- | ----------------------------------------------------- |
| `redeemx.admin.gen`    | Allows generating new codes or templates                  |
| `redeemx.admin.modify` | Allows modifying codes and templates                  |
| `redeemx.admin.delete` | Allows deleting codes and templates                   |
| `redeemx.admin.preview`| Allows previewing codes or viewing usage stats        |
| `redeemx.admin.renew`  | Allows renewing expired codes                         |
| `redeemx.admin.list`   | Allows getting list of codesor template               |
| `redeemx.admin.reload` | Allows reloading plugin configuration (`/rcx reload`) |
| `redeemx.admin.*`      | Grants all admin permissions listed above.            |

!!! example "Example"
    ```
    /lp group admin permission set redeemx.admin.use.gen true
    ```
    ```
    /lp group admin permission set redeemx.admin.use.modify true
    ```
    ```
    /lp group admin permission set redeemx.admin.use.delete true
    ```
    ```
    /lp group admin permission set redeemx.admin.use.preview true
    ```