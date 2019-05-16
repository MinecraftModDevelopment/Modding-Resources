# Opaque, Normal, and Full cubes.

The block class has several methods for describing what type of cube the block is. These methods are not very descriptive, and are generally considered to be poorly named. Here is a general breakdown explaining these methods, and when you should use them.

- `isOpaqueCube` - Used to describe if your block lets light through it. This should be true if your block isn't a perfect 1x1x1 cube, or if you have transparent or translucent pixels in the texture. If your block makes the faces of nearby blocks see through, you likely forgot to set this to false.
- `isFullCube` - Used to describe if the block is a full cube. This is used by game logic for things like collision, suffocation, and lighting.
- `isNormalCube` - This one is a bit all over the place. Some say it is a duplicate of isFullCube, however it is used for some parts of game logic. For example, it is used to determine if water mobs can spawn inside of it, or if comparators can pull a redstone signal from it.