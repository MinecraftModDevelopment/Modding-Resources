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
https://darkhax.net/tag/mc-mod-tutorial?MMDDevPins

https://wiki.mcjty.eu/modding/index.php?title=Main_Page - 1.10.2/1.11/1.12 Documentation 

https://github.com/McJty/ModTutorials/ - 1.8.9/1.9.4/1.10.2/1.11/1.12

https://shadowfacts.net/tutorials/forge-modding-112/ - 1.10.2/1.11.2/1.12

https://github.com/Shadows-of-Fire/How2Mod/blob/master/Instructions.txt/

https://github.com/TheGreyGhost/MinecraftByExample/ 1.8.9/1.10.2/1.11.2

[https://bedrockminer.jimdo.com/modding-tutorials](https://web.archive.org/web/20170629194638/https://bedrockminer.jimdo.com/modding-tutorials) 1.7.10/1.8.9

[http://www.wuppy29.com/minecraft/modding-tutorials/forge-modding/](https://web.archive.org/web/20181007042911/http://www.wuppy29.com/minecraft/modding-tutorials/forge-modding/) 1.3.2/1.4/1.5.1/1.6/1.7.10/1.8.9

### Java for complete beginners
https://www.youtube.com/playlist?list=PL9DF6E4B45C36D411

https://docs.oracle.com/javase/tutorial/java/concepts/

https://docs.oracle.com/javase/tutorial/java/javaOO/

https://docs.oracle.com/javase/tutorial/java/nutsandbolts/

The Oracle docs can be technical at times, if you're an absolute beginner, you might find something like CodeAcademy to be more helpful.

### Useful Gradle settings for Minecraft

Where things go:  
The block itself goes in the minecraft block.  
The respective vars get defined in your gradle.properties, I suggest NOT putting the ones starting mc_ in your per project gradle.properties, do it in your user gradle.properties instead (That's the one in ~/.gradle on linux, or %userprofile%/.gradle on windows).

What it does:
1) Lets you define how much RAM is given to the client or server when they're run with gradlew runClient/runServer.
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

### Argument to remove "Unable to instantiate org.fusesource.jansi.WindowsAnsiOutputStream" 
```gradle
-Dlog4j.skipJansi=true
```

### CurseForge 
endpoint
```gradle
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

### Adding Dependencies to your @Mod annotation
Adding Dependencies to your @Mod annotation is as simple as setting the dependencies field to this:
dependencies="required-after:forge@[minVersion,maxVersion)"

Multiple dependencies are separated using ;, min and max version are optional. [, ] = included, (,) = excluded versions. you can also leave the min or max fields empty or omit the whole version range.
keywords
 after = load this mod after the one specified, if present
before = load this mod before the one specified, if present.

Keywords can be prefixed with required-, which will force the specified modid to be present.

For more info on the version ranges see https://docs.oracle.com/middleware/1212/core/MAVEN/maven_version.htm#MAVEN402

### Version ranges
Format used in version ranges strings (for dependencies for example)
https://maven.apache.org/enforcer/enforcer-rules/versionRanges.html

### Example buildscript for using Forge's ContainedDeps system
https://github.com/JamiesWhiteShirt/clothesline/blob/master/build.gradle

### Item Rendering with GL
With the release of Forge 14.23.2.2638, a proper way to render items with GL was implemented. Using this system is much simpler than the old system, which required a TileEntity, and does not allow access to the ItemStack.

[More information and implementation here](https://gist.github.com/Shadows-of-Fire/aadd7a27d7df1c2f43eb226ea3b2dcdd)

### Git basics
###### Basic challenges to learn Git
https://try.github.io/levels/1/challenges/1

###### Git clients
Easy for new users  
[Github Desktop](https://desktop.github.com/)

Mid-ranged  
[Sourcetree](https://www.sourcetreeapp.com/)

Semi-advanced  
[GitKraken](https://www.gitkraken.com)


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


Note that version and jarname needed for the `deobfCompile` relies on the jarname being in the format: `modid-mcversion-modversion.jar`. This is not always the case, meaning that it can be difficult to figure out the correct infomation to add. There is a tool that figures out this infomation for you:
https://github.com/Wyn-Price/CurseForge-Maven-Helper/
### A way to check if you are running in a dev environment
```java
public static boolean isDevEnv() {
    return (Boolean) Launch.blackboard.get("fml.deobfuscatedEnvironment");
}
```

### Tool to help work out Curseforge's Maven.
 Works out dependencies and gives you what to put in your build.gradle    
 Wyn-Price's client side tool [releases](https://github.com/Wyn-Price/CurseForge-Maven-Helper/releases/latest) [source](https://github.com/Wyn-Price/CurseForge-Maven-Helper/)    
 Darkhax's FireFox extension [releases](https://addons.mozilla.org/en-US/firefox/addon/bettercf)
 
### Setting up a modding env. in Intellij
https://streamable.com/hlxy0

### Why you should never use OpenGL directly or GlStateManager.pushAttrib/popAttrib
https://gist.github.com/JamiesWhiteShirt/ff2521936a83ebc10fd6893e206a6770

### Updating gradle version to 4.9
```gradlew wrapper --gradle-version 4.9```

### Means of integration with other mods
https://gist.github.com/strikerrocker/873f81e686f391662f39b83efee136ff

### Converting lang from <1.13 to 1.13.
https://github.com/ichttt/MCLang2Json
`marco@invader ~ % sed -Ee '1i {' -e '$a }' -e 's|^tile\.|block.|g;s|\.name=|=|g;s|["\]|\\\0|g;s|^([^=]*)?=(.*)$|  "\1": "\2",|g;$ s|,$||g'
some.key=abc;',\ 238"";'2                       `

result
`{
  "some.key": "abc;',\\ 238\"\";'2"
}`

### Why does't my Event Handler Work!!??
https://cdn.discordapp.com/attachments/179315645005955072/475010493824892948/unknown.png

## Registering using @ObjectHolder annotation on class
```java
@GameRegistry.ObjectHolder(WingsMod.ID)
public final class WingsItems {
    private WingsItems() {}

    public static final Item FAIRY_DUST = Items.AIR;

    public static final Item AMETHYST = Items.AIR;

    public static final Item BAT_BLOOD = Items.AIR;
```
Those field names are the registry names
ObjectHolder on class has forge looks at fields for reference types that are a registry type

### Tool doing remappings 
 https://github.com/MinecraftForge/Remapper
 
### 1.12 snapshots to stable remappings
https://gist.github.com/strikerrocker/1e31558b35dc65c49fb56fddca9fcf5d

### Using the debugger
Intellij: 
https://www.jetbrains.com/help/idea/debugging-your-first-java-application.html
https://www.jetbrains.com/help/idea/debugging-code.html

Eclipse:
http://www.vogella.com/tutorials/EclipseDebugging/article.html
https://www.eclipse.org/community/eclipse_newsletter/2017/june/article1.php

### Querying MCP mappings and its history
If you need to query MCP names or their history, or help give a name to something that has not been named yet, you may want to use the bot they have in this server. Read their readme and use !help to learn more (and keep the bot spam in the dedicated channel.) -- https://discord.gg/h4whGT9
 
### MCP mapping tools
http://mcp.thiakil.com/index.html

http://bspk.rs/MC/MCPMappingViewer/index.html

### Minecraft dev IDEA plugin
https://plugins.jetbrains.com/plugin/8327/

Heads up: an update changed the default inspection settings to disable the Minecraft Forge inspections. If you somehow reset your settings then you will lose the inspections. If you use these inspections, you can enable them by going to Settings > Editor > Inspections, then finding the Minecraft Forge group and enabling the ones you were using.

### Java naming conventions
http://www.oracle.com/technetwork/java/codeconventions-135099.html

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

### Example of how to register a data fixer
 to migrate your tile entity to a new ID, in case you have registered it in the wrong domain and are seeing the error now: https://github.com/TeamTwilight/twilightforest/blob/3d141a2bfb312e1d4292ab1ebc21880703945ff7/src/main/java/twilightforest/TwilightForestMod.java#L134-L196

### ObjectHolders and registry class
Simple explanation and exemple of an object holder and registry class
https://gist.github.com/TehNut/dad98543d72d9338d780a24e087e9c7e/

### Information on the vanilla debug profiler
https://redd.it/5mxn51/

### Why are 32 x 32 textures bad?
https://latmod.com/moddingtutorials/non-16x-textures/

### Smelting JSON Recipe 1.12
Allows you to use JSONs for smelting recipes on 1.12
The JSONs follow the exact same format as vanilla 1.13 ones.
https://gist.github.com/Bluexin/c4960cf81b7720afbda0b1fbcfdd0450

### Naming assets
names in mod assets *MUST* be in lower case

### Recipe conditions
Great resource for all forms of recipe json conditions
https://github.com/Vazkii/Botania/tree/master/src/main/resources/assets/botania/recipes

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

### @SideOnly annotation
Gist that glosses over a lot of the @SideOnly annotation system.
https://gist.github.com/TehNut/4e7b60e0a43c39a709b8b59ae48cb493

### Converting exported Techne models to other formats
https://gist.github.com/ljfa-ag/cd137f5c741a0cfb0ead

### Forge info by version
![](https://github.com/MinecraftModDevelopment/Modding-Resources/raw/master/Version%20Info.png)

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

### Lang to Json converter
https://tterrag.com/lang2json/

### Condition factories registered from JSON 
https://github.com/MinecraftForge/MinecraftForge/blob/1.12.x/src/test/resources/assets/crafting_system_test/recipes/_factories.json#L8-L10

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

### Preventing remote movement on entities
 set "PreventRemoteMovement" to true on the entity data, i.e. make `item.getEntityData().getBoolean("PreventRemoteMovement")`return true, and magnets should not grab things from your plates. That was agreed upon somewhere in a github issue on ImmEng, and is supported by most mods with magnets

### 1.11 to 1.12 class name changes
https://github.com/ModCoderPack/MCPBot-Issues/wiki/1.11.0-to-1.12.0-migration

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

### isOpaqueCube, isNormalCube, isFullCube ?
isOpaqueCube - should be false if your block isn't a full 1x1x1 cube or has transparent/cutout texture, otherwise your blocks surroundings will look bad

isNormalCube - you don't need to override that. Calls isFullCube.

isFullCube - same thing really, but it handles game logic like suffocation, pushing you out of blocks, and also other render stuff like lighting

basically, these method names (isBlockNormalCube, isNormalCube, isFullCube, isFullBlock, isOpaqueCube) are confusing. Just override these two and you should be fine

### OpenGL11 Rendering Tutorial
http://www.glprogramming.com/red/index.html

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

### Troubleshooting Eclipse development with other mods
https://github.com/MinecraftForge/ForgeGradle/issues/519#issuecomment-423849322

### Collection of Useful Gradle Scripts
https://github.com/MinecraftModDevelopment/Gradle-Collection

### Version Support Coverage by Author
https://docs.google.com/spreadsheets/d/1gQY1EzYwOXpfehluqujwh_32regA798RHmdlgG6rdKU/edit#gid=0

### Curse Profit Calculator 
https://cobalt.darkhax.net/curse-profit-calc/

### Curse Author Statistics (Modmuss's CurseTracker)
https://cursetracker.modmuss50.me/
