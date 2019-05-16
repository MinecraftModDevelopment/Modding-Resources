### Getting a fluid texture
```java
TextureAtlasSprite texture = ModelLoader.defaultTextureGetter().apply(fluid.getFluid().getFlowing(fluid));
```

### Preventing specific entities from interacting with your fluid
```java
public Boolean isEntityInsideMaterial(IBlockAccess world, BlockPos blockpos, IBlockState iblockstate, Entity entity, double yToTest, Material materialIn, boolean testingHead) {
        //In this example, prevents Players from interacting with the fluid
        return !(entity instanceof EntityPlayer);
    }
```
You can override this method in your Fluid's Block class to make it so that specific entites don't interact with your fluid. The above example makes it so that players do not interact with the fluid, but other entities will continue to do so. You may need additional checks to ensure that other entities are actually inside the fluid, because the example above as written will always return true for entites other than the player, even if they are not actually inside the fluid.
