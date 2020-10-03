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
