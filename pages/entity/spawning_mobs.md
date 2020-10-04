# Spawning Mobs & Entities
This document covers the basics of how to spawn a mob or entity into the game. 

## 1.12.2

When spawning a mob it is very important to use the existing helper methods within the game. These methods are patched by Forge and other mods to allow various events and effects to trigger. The correct method for this is `ItemMonsterPlacer#spawnCreature`, which is used by mob spawner blocks, dispensers, spawn eggs, and some portal blocks. The following example shows how a custom item can spawn an entity when it is clicked.

```java
    public ActionResult<ItemStack> onItemRightClick (World world, EntityPlayer player, EnumHand hand) {
        
        // Get the itemstack that is being clicked. This is needed later on.
        ItemStack stack = player.getHeldItem(hand);
        
        // Check if this is happening on the client or the server.
        // Spawning entities on the client can result in ghost entities.
        if (!world.isRemote) {
            
            // Spawn the zombie on top of the player entity. This will fire all the events.
            ItemMonsterPlacer.spawnCreature(world, EntityList.getKey(EntityZombie.class), player.posX, player.posY, player.posZ);
        }
        
        // Tell the game that the item was used successfully.
        return new ActionResult<>(EnumActionResult.SUCCESS, stack);
    }
```

In some situatiosn you may also want to change properties of the entity when it is spawned. This can be done by using the return result from the `ItemMonsterPlacer#spawnCreature` method and setting the properties there. Keep in mind that this method is nullable, meaning if the entity fails to respawn the result will be null. 

```java
    public ActionResult<ItemStack> onItemRightClick (World world, EntityPlayer player, EnumHand hand) {
        
        // Get the itemstack that is being clicked. This is needed later on.
        ItemStack stack = player.getHeldItem(hand);
        
        // Check if this is happening on the client or the server.
        // Spawning entities on the client can result in ghost entities.
        if (!world.isRemote) {
            
            // Spawn the zombie on top of the player entity. This will fire all the events.
            Entity spawnedEntity = ItemMonsterPlacer.spawnCreature(world, EntityList.getKey(EntityZombie.class), player.posX, player.posY, player.posZ);
            
            // Check if the entity spawned properly.
            if (spawnedEntity != null) {
                
                // Give the entity a custom name tag.
                spawnedEntity.setCustomNameTag("Some Zombie");
            }
        }
        
        // Tell the game that the item was used successfully.
        return new ActionResult<>(EnumActionResult.SUCCESS, stack);
    }
```

The above code is only for spawning mobs. This means that the entity spawned must be registered with the spawn egg registry. In some situations you may want to spawn an entity that is not a mob, like a fireball. There are no special methods for this so you can spawn the mob into the world as you would regularly. 

```java
    // Check if this is happening on the client or the server.
    // Spawning entities on the client can result in ghost entities.
    public ActionResult<ItemStack> onItemRightClick (World world, EntityPlayer player, EnumHand hand) {
        
        // Get the itemstack that is being clicked. This is needed later on.
        ItemStack stack = player.getHeldItem(hand);
        
        if (!world.isRemote) {
            
            // Create a new fireball entity. We set the shooter entity and the acceleration.
            EntityFireball fireball = new EntitySmallFireball(world, player, 0f, 1f, 0f);
            
            // Set the position of the fireball to above the player.
            fireball.setPositionAndRotation(player.posX, player.posX + player.eyeHeight + 1, player.posZ, player.prevRotationYawHead, player.rotationPitch);
            
            // Spawn the entity into the world.
            world.spawnEntity(fireball);
        }
        
        // Tell the game that the item was used successfully.
        return new ActionResult<>(EnumActionResult.SUCCESS, stack);
    }
 ```
