# 📦 Adding RedeemX API Dependency

To use the RedeemCodeX API in your plugin, include the following dependency in your project setup.

---

## 🧱 Repositories

Add JitPack and Maven Central to your repositories configuration:

=== "Gradle"

    ```kotlin
    repositories {
        mavenCentral()
        maven { url = uri("https://jitpack.io") }
    }
    ```
=== "Maven"

    ```xml
    <repositories>
        <repository>
            <id>jitpack.io</id>
            <url>https://jitpack.io</url>
        </repository>
    </repositories>
    ```

---

## 🔗 Dependency

Add the API dependency to your project.

!!! warning
    Replace `VERSION` with the actual version or tag (e.g., `1.0.0`) on GitHub.

=== "Gradle"

    ```kotlin
        dependencies {
            compileOnly("com.github.ItzYashvardhan:RedeemCodeX-API:VERSION")
        }
    ```

=== "Maven"

    ```xml
        <dependencies>
            <dependency>
                <groupId>com.github.ItzYashvardhan</groupId>
                <artifactId>RedeemCodeX-API</artifactId>
                <version>VERSION</version>
            </dependency>
        </dependencies>
    ```

---

## ✅ Verifying JitPack

Make sure your project syncs successfully. If you see issues:

* Double-check that the `VERSION` exists on GitHub.
* Check for typos in the group ID or artifact name.
* Confirm you’re using the correct build tool syntax.

---

## 🔄 Keeping Up to Date

To stay on the latest version:

* Watch the [RedeemCodeX-API GitHub repository](https://github.com/ItzYashvardhan/RedeemCodeX-API)
* Update your dependency when new tags are published

