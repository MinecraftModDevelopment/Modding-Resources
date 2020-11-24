# `ExistingFileHelper`
---

To be able to validate pre-existing resources when generating data, Forge uses a helper class to determine if a file exists in a specified location. This helper class consists of five methods, two of which are for public use, and one which is visible for testing purposes.

Method | Description 
:---: | ---
`getManager` | Gets the current resource manager to search for whether it's from client assets or sever datapacks.
`getLocation` | Constructs the location of the file. It takes in a base to get the actual simple location, a prefix to get a subfolder the location might exist in, and a suffix to determine the file extension.
`exists` | Determines whether a file exists in the given pack type (assets or data).
`getResource` | Used for testing whether the resource is available to grab. If not, throws an exception.
`isEnabled` | Returns true if validation is enabled.

The only ones that should be used by default are `exists` and `isEnabled`. A reference to the helper can be grabbed from the `GatherDataEvent`.

## Attaching Resources
---

Resources can be attached through the args in the data block of `build.gradle`. Here's a snipped of it's default configuration.

```gradle
data {
    workingDirectory project.file('run')

    property 'forge.logging.markers', 'SCAN,REGISTRIES,REGISTRYDUMP'

    property 'forge.logging.console.level', 'debug'

    args '--mod', 'examplemod', '--all', '--output', file('src/generated/resources/')

    mods {
        examplemod {
            source sourceSets.main
        }
    }
}
```

To be able to grab resources from your acutal mod resources, you can do simply by adding `--existing` with the file location of your resources folder (usually `src/main/resources`) like so:

```gradle
args '--mod', 'examplemod', '--all', '--output', file('src/generated/resources/'), --existing, file('src/main/resources/')
```

You can add more existing file locations by simply repeating the process with the location of other resources you would like to consider.

### Attaching Generated Resources

If you would like to consider the generated resources without moving them, that can be arranged by simply adding it in to the main resources `srcDirs` like so:

```gradle
sourceSets {
    main.resources.srcDirs += 'src/generated/resources'
}
```

> Note: This will need to match up with the exact location of the output provided in the arguments of the data block.

## Attaching Modded Resources (35.1.3+)

To add modded resources to your workspace, you can append `--existing-mod <modid>` to the end of the args within the data block like so:

```gradle
args '--mod', 'examplemod', '--all', '--output', file('src/generated/resources/'), --existing, file('src/main/resources/'), --existing-mod 'dependencymod'
```

If you do not specify Forge resources, they will be added by default.

## Attaching Forge Resources Prior to 35.1.3

Forge resources are also not attached by default. However, there is a slight issue to to this due to a cyclical dependency. If the dependences are called after the minecraft block, then the minecraft block won't exist when it tries to add the argument. On the other handle, if the dependencies are called first, the minecraft block will not have been constructed yet.

To get around this until Forge decides to patch it, a bit of hacky gradle will be used via `project.afterEvaluate`. First, we will grab the args for the data block and add another existing parameter to it. We will then grab the minecraft configuration and find the forge resources. We will need to grab the first instance of the value as each `existing` option is bound to a string and not a list. That is queued afterwards.

This block should be added after the dependency and minecraft blocks:

```gradle
project.afterEvaluate {
    minecraft.runs.data.args('--existing', configurations.minecraft.asPath.split(":").toList().find { it.contains("forge") }.split(";")[0])
}
```

Now rerun your gradle dependencies and the regen the runs and you should be able to use yours and Forge's resources in your data providers.
