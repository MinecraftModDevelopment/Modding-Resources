### AI Task
The red task will run when the entity#getAttackTarget != null. And as long as the target is null, the green tasks will run in order to set an attack target.
so if you want to set a target, you add a target task. But if you want to modify how they attack or add a task to move somewhere, you add a task.

![alt text](https://cdn.discordapp.com/attachments/179315645005955072/399651904428310528/tasks.png)

### Basic challenges to learn Git
https://try.github.io/levels/1/challenges/1

### Code recipe to JSON generator
https://gist.github.com/williewillus/a1a899ce5b0f0ba099078d46ae3dae6e

https://crafting.thedestruc7i0n.ca/

### Mod Tutorials
https://github.com/McJty/ModTutorials

https://shadowfacts.net/tutorials/forge-modding-112/

### ObjectHolders and registry class
Simple explanation and exemple of an object holder and registry class
https://gist.github.com/TehNut/dad98543d72d9338d780a24e087e9c7e

### Live class reloading
Use live class reloading to avoid having to restart the game for most changes in your code. Start the game with a debugger, make your changes, save, then (depending on your IDE) do\nIntellij: Click the button left to the launch configurations (Build Project). You will be prompted to reload classes. Accept.\nEclipse: Select Project -\u003e Build All\n\nFor live resource reloading, build your project, then press F3+T in-game.

### Gradle generation of forge javadocs
http://maven.thiakil.com/forge-1.12-javadoc/

### Gradle runner setting
http://i.nentify.me/xvdv2.png

### JEI Discord to ask questions
https://discord.gg/EevEdSG

### Modding guide by Shadows-of-Fire 
https://github.com/Shadows-of-Fire/How2Mod/blob/master/Instructions.txt


### Polygon function
https://stackoverflow.com/questions/8721406/how-to-determine-if-a-point-is-inside-a-2d-convex-polygon#8721483

### Converting old recipe code into json
https://gist.github.com/williewillus/a1a899ce5b0f0ba099078d46ae3dae6e

### Condition factories registered from JSON 
https://github.com/MinecraftForge/MinecraftForge/blob/1.12.x/src/test/resources/assets/crafting_system_test/recipes/_factories.json#L8-L10

### CurseForge maven endpoint
```Gradle
repositories {
maven {
        //fallback for almost everything, this is CurseForge :P
        name = "CurseForge"
        url = "https://minecraft.curseforge.com/api/maven/"
    }
}

. . .

dependencies {
compile "<curse-slug>:<jarname>:<version>"
}
```

### Using Git
stage `git add`, commit `git commit -m \"message\"`, push `git push`

### Minecraft energy types conversion rates
https://gist.github.com/DeflatedPickle/403e1eb0bb0bed7f2509142e63630726

### Minecraft Annotations
https://github.com/mezz/MinecraftAnnotations

### List of mod ideas
https://docs.google.com/document/d/10EDeU8_gGPBNcmZg_m9QTCuiRee-Ifw8dNWUTlGqWlg/edit?usp\u003ddrivesdk

### Deprecation
It is deprecated, as in you should not CALL it.
As Mojang is still working on the internals to move away from this and other functions in Block in favor of BlockState they have marked a lot of Functions @Deprecated in a "Do not call this but if you MUST override it, then do so"
Minecraft has been, is, and always will be a work in progress. Its just one of the quirks.

### Animations in ressource packs
http://minecraft.gamepedia.com/Tutorials/Creating_a_resource_pack#Animation_Properties


### Information on the vanilla debug profiler
https://redd.it/5mxn51

### 1.10.2 exemple mod
https://github.com/McJty/ModTutorials/tree/1.10.2

### Ressources to start Java
https://docs.oracle.com/javase/tutorial/java/concepts/
https://docs.oracle.com/javase/tutorial/java/javaOO/
https://docs.oracle.com/javase/tutorial/java/nutsandbolts/
The oracle docs can be technical at times, if you're an absolute beginner, you might find something like CodeAcademy to be more helpful.

### MinecraftForge documentation
https://mcforge.readthedocs.io/en/latest/

### Rendering a basic block
http://pastebin.com/N1YRRcm7

### Summoning mobs
```java
public static void summonMobsOnBreakBlock(EntityMob mob, int loop, World worldIn, BlockPos pos) throws IllegalAccessException, InstantiationException, NoSuchMethodException, InvocationTargetException {


            for (int i = 0; i < loop; i++) {
                mob=mob.getClass().getConstructor(World.class).newInstance(worldIn);
                mob.setPosition(pos.getX(), pos.getY(), pos.getZ());
                mob.setAlwaysRenderNameTag(true);
                worldIn.spawnEntityInWorld(mob);
            }

    }
```

### Neighbor block caching for stuff like context-sensitive render states
```java
public class NeighborCache<T> {
    
    Map<BlockPos, T> cache = new HashMap<>();
    Function<BlockPos, T> generator;
    BlockPos basePos;
    
    public NeighborCache(BlockPos pos, Function<BlockPos, T> generator) {
        this.basePos = pos;
        this.generator = generator;
    }
    
    public T get(int x, int y, int z) {
        return get(new BlockPos(x,y,z));
    }
    
    public T get(BlockPos relPos) {
        return getOrPut(relPos);
    }
    
    public T get(EnumFacing dir) {
        return get(BlockPos.ORIGIN.offset(dir));
    }
    
    public T get(EnumFacing dir1, EnumFacing dir2) {
        return get(BlockPos.ORIGIN.offset(dir1).offset(dir2));
    }
    
    public T get(EnumFacing dir1, EnumFacing dir2, EnumFacing dir3) {
        return get(BlockPos.ORIGIN.offset(dir1).offset(dir2).offset(dir3));
    }
    
    private T getOrPut(BlockPos relPos) {
        if(!cache.containsKey(relPos))
            cache.put(relPos, generator.apply(relPos.add(basePos)));
        return cache.get(relPos);
    }
    
}
```
Usage:
```java
NeighborCache<IBlockState> stateCache = new NeighborCache<>(pos, (p) -> world.getBlockState(p));
NeighborCache<TileEntity> tileCache = new NeighborCache<>(pos, (p) -> world.getTileEntity(p));
```

### Minecraft dev IDEA plugin
https://plugins.jetbrains.com/plugin/8327

### Troubleshooting Block and Item Rendering
http://greyminecraftcoder.blogspot.com.au/2015/03/troubleshooting-block-and-item-rendering.html

### Mob ore drop
```java
public class MobOreDrops {

    @SubscribeEvent
    public void onEntityDrop(LivingDropsEvent event) {
        if(event.entityLiving instanceof EntityCreature) {
            Random r = new Random();
            List<ItemStack> ores = OreDictionary.getOres("oreIron");
            if (ores == null || ores.size() <= 0) { return; }
            Item oreItem = (Item) ores.get(0).getItem();
            event.entityLiving.dropItem(oreItem, r.nextInt(2));
        }
    }
    
}
```
### Rendering Handler
```java
RenderingRegistry.registerEntityRenderingHandler(GolemBase.class, new IRenderFactory<GolemBase>() 
{
    @Override
    public Render<? super GolemBase> createRenderFor(RenderManager manager) 
    {
        return new RenderGolem(manager);
    }
});
```
### Models
http://jabelarminecraft.blogspot.com/p/complex-entity-models-including.html

### Removing sensitive data from your git repo
https://help.github.com/articles/remove-sensitive-data/

### Java for complete beginners
https://www.youtube.com/playlist?list\u003dPL9DF6E4B45C36D411

### Detection system for MCreator mods
http://mdetector.thedragonteam.net/test.html

### Making a flying armor
http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-mods/modification-development/2678865-help-how-to-apply-flight-to-an-armor-in-eclipse-1
more concise but you need to know more Java: http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-mods/modification-development/2650028-trying-to-make-an-item-that-allows-flight#c7

### JSon linter
http://jsonlint.com/

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

### Basic Item Model
```json
{
    "parent": "item/generated",
    "textures": {
        "layer0": "modid:items/texture_name"
    }
}
```

### Darkhax's tutorials
http://tutorials.darkhax.net/

### Useful ASM coremmoding ressources
https://www.youtube.com/watch?v\u003dFgaxnpD-DC4
https://www.youtube.com/watch?v\u003d75_rJYLj5AU
NOT for beginners!!!

### Useful stuff for beginners
https://docs.oracle.com/javase/tutorial/
