### AI Tasks
```java
class MyEntity extends Entity {
    @Override
    protected void initEntityAI() {
        //This will run when this.attackTarget != null.
        tasks.addTask(4, new EntityAIAttackMelee(this, 1.2d, false));
        
        /*
         * When this.attackTarget == null, these tasks will run to find a target.
         * So add a task to targetTasks to change how targeting is done.
         */
        targetTasks.addTask(1, new EntityAIHurtByTarget(this, false, new Class[0]));
        targetTasks.addTask(2, new EntityAINearestAttackableTarget(this, EntityPlayer.class, true));
    }
}
```

