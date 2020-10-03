### Checking a command sender's permission level

```java
sender.canUseCommand(3, this.getName())
```
You can also override `getRequiredPermissionLevel` if you want to set the permission required to run the command