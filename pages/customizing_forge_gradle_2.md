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

### Argument to remove "Unable to instantiate org.fusesource.jansi.WindowsAnsiOutputStream" 
```gradle
-Dlog4j.skipJansi=true
```

### Updating gradle version to 4.9
```gradlew wrapper --gradle-version 4.9```

### CurseForge 
endpoint
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