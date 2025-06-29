# 🔐 Admin Permissions
!!! tip ""
    These permissions should only be granted to trusted staff members or server administrators.




## 🛠️ Admin Permissions
| Node                       | Description                                           |
| -------------------------- | ----------------------------------------------------- |
| `redeemx.admin.use.gen`    | Allows generating new codes or templates              |
| `redeemx.admin.use.modify` | Allows modifying codes and templates                  |
| `redeemx.admin.use.delete` | Allows deleting codes and templates                   |
| `redeemx.admin.use.preview`| Allows previewing codes or viewing usage stats        |
| `redeemx.admin.use.renew`  | Allows renewing expired codes                         |
| `redeemx.admin.use.reload` | Allows reloading plugin configuration (`/rcx reload`) |

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