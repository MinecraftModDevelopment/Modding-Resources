
### Ore Dict match
```java
public static boolean oreDictMatches(ItemStack stack1, ItemStack stack2){
        if (OreDictionary.itemMatches(stack1, stack2, true)){
            return true;
        }
        else {
            int[] oreIds = OreDictionary.getOreIDs(stack1);
            for (int i = 0; i < oreIds.length; i ++){
                if (OreDictionary.containsMatch(true, OreDictionary.getOres(OreDictionary.getOreName(oreIds[i])), stack2)){
                    return true;
                }
            }
        }
        return false;
    }
```

### Adding Dependencies to your @Mod annotation
Adding Dependencies to your @Mod annotation is as simple as setting the dependencies field to this:
dependencies="required-after:forge@[minVersion,maxVersion)"

multiple dependencies are separated using ;, min and max version are optional. [, ] = included, (,) = excluded versions. you can also leave the min or max fields empty or omit the whole version range.
keywords
 after = load this mod after the one specified, if present
before = load this mod before the one specified, if present.

keywords can be prefixed with required-, which will force the specified modid to be present.

for more info on the version ranges see https://docs.oracle.com/middleware/1212/core/MAVEN/maven_version.htm#MAVEN402

### Neighbor block caching for stuff like context-sensitive render states
```java
public final class NeighborCache <T> {
    private final Map<BlockPos, T> cache = new HashMap<>();

    private final BlockPos origin;
    private final Function<BlockPos, T> computer;

    public NeighborCache(BlockPos origin, Function<BlockPos, T> generator) {
        this.origin = origin.toImmutable();
        this.computer = pos -> generator.apply(this.origin.add(pos));
    }

    public NeighborCache(Function<BlockPos, T> generator) {
        this(BlockPos.ORIGIN, generator);
    }

    public T get(BlockPos offset) {
        return cache.computeIfAbsent(offset, computer);
    }

    public T get(int x, int y, int z) {
        return get(new BlockPos(x, y, z));
    }

    public T get(EnumFacing offset) {
        return get(BlockPos.ORIGIN.offset(offset));
    }

    public T get(EnumFacing offset1, EnumFacing offset2) {
        return get(BlockPos.ORIGIN.offset(offset1).offset(offset2));
    }

    public T get(EnumFacing offset1, EnumFacing offset2, EnumFacing offset3) {
        return get(BlockPos.ORIGIN.offset(offset1).offset(offset2).offset(offset3));
    }
}
```
Usage:
```java
NeighborCache<IBlockState> stateCache = new NeighborCache<>(pos, world::getBlockState);
NeighborCache<TileEntity> tileCache = new NeighborCache<>(pos, world::getTileEntity);
```

### A way to check if you are running in a dev environment
```java
public static boolean isDevEnv() {
    return (Boolean) Launch.blackboard.get("fml.deobfuscatedEnvironment");
}
```

#Checking a command sender permission level
```java
sender.canUseCommand(3, this.getName())
```
You can also override `getRequiredPermissionLevel` if you want to set the permission required to run the command

