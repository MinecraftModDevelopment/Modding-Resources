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

### Gradle settings for minecraft

Where things go:
The block itself goes in the minecraft block.
the respective vars get defined in your gradle.properties, I suggest NOT putting the ones starting mc_ in your per project gradle.properties, do it in your user gradle.properties instead (That's the one in .gradle).

What it does:
1) Lets you define how much ram is given to the client or server when they're run with gradlew runClient/runServer.
2) Lets you enter your username/password and/or UUID when in dev mode.
3) Adds "nogui" when running runServer (Comment out/remove if not wanted).


```gradle
  if (project.hasProperty('mc_username')) {
    clientRunArgs += ['--username', project.mc_username]
    if (project.hasProperty('mc_password')) {
      clientRunArgs += ['--password', project.mc_password]
    }
  }
  if (project.hasProperty('mc_uuid')) {
    clientRunArgs += ['--uuid', project.mc_uuid]
  }

  // disable server gui
  serverRunArgs += 'nogui'

  // skip the screen to confirm that you want to load a world with missing registry entries
  serverJvmArgs += '-Dfml.doNotBackup=true'
  clientJvmArgs += '-Dfml.doNotBackup=true'

  // skip having to confirm on server
  serverJvmArgs += '-Dfml.queryResult=confirm'

  //skip jansi warnings in the log
  serverJvmArgs += '-Dlog4j.skipJansi=true'
  clientJvmArgs += '-Dlog4j.skipJansi=true'

  if (project.hasProperty('client_args')) {
    clientJvmArgs += project.client_args
  }
  if (project.hasProperty('server_args')) {
    serverJvmArgs += project.server_args
  }
```

### Item Rendering with GL
With the release of Forge 14.23.2.2638, a proper way to render items with GL was implemented. Using this system is much simpler than the old system, which required a TileEntity, and does not allow access to the ItemStack.

[More information and implementation here](https://gist.github.com/Shadows-of-Fire/aadd7a27d7df1c2f43eb226ea3b2dcdd)

### Gradle setting for missing regsitry entries
```gradle
serverJvmArgs += "-Dfml.doNotBackup=true"
clientJvmArgs += "-Dfml.doNotBackup=true"

serverJvmArgs += "-Dfml.queryResult=confirm"
```
first ones skip the screen to confirm that you want to load a world with missing registry entries, last one does this for the server

### Argument to remove "Unable to instantiate org.fusesource.jansi.WindowsAnsiOutputStream" 
```gradle
-Dlog4j.skipJansi=true
```

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
    deobfCompile "<curse-slug>:<jarname>:<version>"
}
```
Note that version and jarname needed for the `deobfCompile` relies on the jarname being in the format: `modid-mcversion-modversion.jar`. This is not always the case, meaning that it can be difficult to figure out the correct infomation to add. There is a tool that figures out this infomation for you:
https://github.com/Wyn-Price/CurseForge-Maven-Helper/
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

### Converting exported Techne models to other formats
https://gist.github.com/ljfa-ag/cd137f5c741a0cfb0ead

### Gradle sample minecraft block
```gradle
minecraft {
    version = "1.12.2-14.23.1.2611"
    runDir = "run"
    mappings = "snapshot_20180220"
    useDepAts = true
    makeObfSourceJar = false
}
```

### Forge info by version
![](https://cdn.discordapp.com/attachments/179315645005955072/413721810241323018/unknown.png)

### Bitshifting tutorial
http://latmod.com/tutorials/bitshifting/

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

### Getting a fluid texture
```java
TextureAtlasSprite texture = Minecraft.getMinecraft().getTextureMapBlocks().getAtlasSprite(fluid.getFluid().getFlowing(fluid).toString());
```

### Preventing remote movement on entities
 set "PreventRemoteMovement" to true on the entity data, i.e. make `item.getEntityData().getBoolean("PreventRemoteMovement")`return true, and magnets should not grab things from your plates. That was agreed upon somewhere in a github issue on ImmEng, and is supported by most mods with magnets

### 1.11 to 1.12 class name changes
https://github.com/ModCoderPack/MCPBot-Issues/wiki/1.11.0-to-1.12.0-migration

### Config system exemple
https://github.com/MinecraftForge/MinecraftForge/blob/1.12.x/src/test/java/net/minecraftforge/debug/ConfigTest.java

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

### .gitignores for everything
https://www.gitignore.io/ 

### Useful ASM coremodding ressources
https://www.youtube.com/watch?v=FgaxnpD-DC4/

https://www.youtube.com/watch?v=75_rJYLj5AU/

*NOT FOR BEGINNERS!!!*

### Polygon function
https://stackoverflow.com/questions/8721406/how-to-determine-if-a-point-is-inside-a-2d-convex-polygon#8721483

#Checking a command sender permission level
```java
sender.canUseCommand(3, this.getName())
```
You can also override `getRequiredPermissionLevel` if you want to set the permission required to run the command

### Animations in resource packs
http://minecraft.gamepedia.com/Tutorials/Creating_a_resource_pack#Animation_Properties

### Rendering a basic block
http://pastebin.com/N1YRRcm7

### OpenGL11 Rendering Tutorial
http://www.glprogramming.com/red/index.html

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
### Rendering Handler registry
```java
RenderingRegistry.registerEntityRenderingHandler(GolemBase.class, RenderGolem::new);
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

### Coding practice
https://www.hackerrank.com/

