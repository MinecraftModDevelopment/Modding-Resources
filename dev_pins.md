### How to make code blocks with syntax highlighting:
\```java  
CODE HERE  
\```  
Full formatting guide here https://support.discordapp.com/hc/en-us/articles/210298617

### 1.13 Changes/Primer
https://gist.github.com/williewillus/353c872bcf1a6ace9921189f6100d09a

### List of mod ideas
https://docs.google.com/document/d/10EDeU8_gGPBNcmZg_m9QTCuiRee-Ifw8dNWUTlGqWlg/

### Mod Tutorials/Guides
https://tutorials.darkhax.net/pages/tutorials/

https://wiki.mcjty.eu/modding/index.php?title=Main_Page - 1.10.2/1.11/1.12 Documentation 

https://github.com/McJty/ModTutorials/ - 1.8.9/1.9.4/1.10.2/1.11/1.12

https://shadowfacts.net/tutorials/forge-modding-112/ - 1.10.2/1.11.2/1.12

https://github.com/Shadows-of-Fire/How2Mod/blob/master/Instructions.txt/

https://github.com/TheGreyGhost/MinecraftByExample/ 1.8.9/1.10.2/1.11.2

https://bedrockminer.jimdo.com/modding-tutorials/ 1.7.10/1.8.9

http://www.wuppy29.com/minecraft/modding-tutorials/forge-modding/#sthash.WeP0PGW2.dpbs/ 1.3.2/1.4/1.5.1/1.6/1.7.10/1.8.9

### Java for complete beginners
https://www.youtube.com/playlist?list=PL9DF6E4B45C36D411

https://docs.oracle.com/javase/tutorial/java/concepts/

https://docs.oracle.com/javase/tutorial/java/javaOO/

https://docs.oracle.com/javase/tutorial/java/nutsandbolts/

The oracle docs can be technical at times, if you're an absolute beginner, you might find something like CodeAcademy to be more helpful.

### Git basics
###### Basic challenges to learn Git
https://try.github.io/levels/1/challenges/1

###### Git clients
Semi advanced  
https://www.gitkraken.com/

Easy for new users  
https://desktop.github.com/

Mid ranged  
https://www.sourcetreeapp.com/

###### Using Git
To clone an entire repo.  
``git clone https://github.com/user/repo.git``

To find the clone url for a repo look for this green button on Github then click it and copy the link provided.  
![alt text](https://cdn.discordapp.com/attachments/197165501741400064/401824959556747264/Screenshot_2018-01-13_19-48-03.png)

To clone a repo with a certain branch.  
``git clone -b branchName https://github.com/user/repo.git``

To stage all changes.  
``git add *``

To stage some changes.  
``git add ifItsInAFolder/file.txt``

To commit changes to the local repo with a message.  
``git commit -m "Here is a nice message"``

To push all changes to github.  
``git push``

###### Removing sensitive data from your git repo
https://help.github.com/articles/remove-sensitive-data/

### MinecraftForge documentation
https://mcforge.readthedocs.io/en/latest/

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

### A way to check if you are running in a dev environment
```java
public static boolean isDevEnv() {
    return (Boolean) Launch.blackboard.get("fml.deobfuscatedEnvironment");
}
```

### MCP mapping tools
http://mcp.thiakil.com/index.html

http://bspk.rs/MC/MCPMappingViewer/index.html

### Minecraft dev IDEA plugin
https://plugins.jetbrains.com/plugin/8327/

### Minecraft energy types conversion rates
https://gist.github.com/DeflatedPickle/403e1eb0bb0bed7f2509142e63630726/

### Live class reloading
Use live class reloading to avoid having to restart the game for most changes in your code. Start the game with a debugger, make your changes, save, then (depending on your IDE)

Intellij: Click the button left to the launch configurations (Build Project). You will be prompted to reload classes. Accept.

Eclipse: Your IDE is likely configured to build automatically, all you have to do is save. If not, select Project -> Build All.

For live resource reloading, build your project first, then press F3+T in-game.

### Gradle generation of forge javadocs
http://maven.thiakil.com/forge-1.12-javadoc/

### Minecraft Annotations
https://github.com/mezz/MinecraftAnnotations/

### ObjectHolders and registry class
Simple explanation and exemple of an object holder and registry class
https://gist.github.com/TehNut/dad98543d72d9338d780a24e087e9c7e/

### Information on the vanilla debug profiler
https://redd.it/5mxn51/

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

### JSon linter
http://jsonlint.com/

### JEI Discord to ask questions
https://discord.gg/EevEdSG

### Recipe creation/conversion tools
###### Vanilla recipe generation tool (replace the items with the mods own)
https://crafting.thedestruc7i0n.ca/

###### Converting old recipe code into json
https://gist.github.com/williewillus/a1a899ce5b0f0ba099078d46ae3dae6e

### Condition factories registered from JSON 
https://github.com/MinecraftForge/MinecraftForge/blob/1.12.x/src/test/resources/assets/crafting_system_test/recipes/_factories.json#L8-L10

### Detection system for MCreator mods
http://mdetector.thedragonteam.net/test.html

### Mob stuff
###### AI Task
The red task will run when the entity#getAttackTarget != null. And as long as the target is null, the green tasks will run in order to set an attack target.
so if you want to set a target, you add a target task. But if you want to modify how they attack or add a task to move somewhere, you add a task.

![alt text](https://cdn.discordapp.com/attachments/179315645005955072/399651904428310528/tasks.png)

###### Summoning mobs
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

###### Mob ore drop
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

### Useful ASM coremodding ressources
https://www.youtube.com/watch?v=FgaxnpD-DC4/

https://www.youtube.com/watch?v=75_rJYLj5AU/

*NOT FOR BEGINNERS!!!*

### Polygon function
https://stackoverflow.com/questions/8721406/how-to-determine-if-a-point-is-inside-a-2d-convex-polygon#8721483

### Animations in resource packs
http://minecraft.gamepedia.com/Tutorials/Creating_a_resource_pack#Animation_Properties

### Rendering a basic block
http://pastebin.com/N1YRRcm7

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
### Models 1.7.2
http://jabelarminecraft.blogspot.com/p/complex-entity-models-including.html

### Basic Item Model
```json
{
    "parent": "item/generated",
    "textures": {
        "layer0": "modid:items/texture_name"
    }
}
```
### Troubleshooting Block and Item Rendering
http://greyminecraftcoder.blogspot.co.uk/2015/03/troubleshooting-block-and-item-rendering.html

### Making a flying armor
http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-mods/modification-development/2678865-help-how-to-apply-flight-to-an-armor-in-eclipse-1  
more concise but you need to know more Java: http://www.minecraftforum.net/forums/mapping-and-modding/minecraft-mods/modification-development/2650028-trying-to-make-an-item-that-allows-flight#c7
