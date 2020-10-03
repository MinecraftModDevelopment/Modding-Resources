### A way to check if you are running in a dev environment

```java
public static boolean isDevEnv() {
    return (Boolean) Launch.blackboard.get("fml.deobfuscatedEnvironment");
}
```
