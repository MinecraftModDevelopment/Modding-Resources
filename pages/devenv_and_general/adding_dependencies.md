### Adding Dependencies to your @Mod annotation (1.12 and below)

Adding Dependencies to your @Mod annotation is as simple as setting the dependencies field to this:
dependencies="required-after:forge@[minVersion,maxVersion)"

multiple dependencies are separated using ;, min and max version are optional. [, ] = included, (,) = excluded versions. you can also leave the min or max fields empty or omit the whole version range.
keywords
 after = load this mod after the one specified, if present
before = load this mod before the one specified, if present.

keywords can be prefixed with required-, which will force the specified modid to be present.

for more info on the version ranges see https://docs.oracle.com/middleware/1212/core/MAVEN/maven_version.htm#MAVEN402

### Adding Dependencies to your mods.toml (1.13 and above)

You can declare dependencies on other mods in your `mods.toml`. Each dependency is headed by a `[[dependencies.<modid>]]`, where `<modid>` should be the modid of the mod that requires the dependency (in most cases, you only have one mod in your `mods.toml`)

The following are the properties which can be present under each `[[dependencies.<modid>]]` header.

| Property       | Default Value | Description                                                                                                                                                                                            |
|:--------------:|:-------------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `modId`        | **mandatory** | The modid of the dependency.                                                                                                                                                                           |
| `mandatory`    | **mandatory** | A boolean value, whether to stop the game from loading if this dependency does not exist.                                                                                                              |
| `versionRange` | `""`          | The acceptable version range of the dependency, expressed as a [Maven version spec][version_spec]. An empty string is an unbounded version range, which matches any version.                           |
| `ordering`     | `"NONE"`      | The order in which this mod must load relative to this dependency. The valid values are `BEFORE` (mod must load before dependency), `AFTER` (must load after), and `NONE` (does not care about order). |
| `side`         | `"BOTH"`      | The physical side in which this dependency must be present. The valid values are `CLIENT` (present on the client), `SERVER` (present on the dedicated server), and `BOTH` (present on both sides).     |

An example dependency for the mod `alchemia`, for the mod with id `bookcase`, which is mandatory, server-side-only, and only accepts versions equal to and above `1.0` and below `2.0`:

```toml
[[dependencies.alchemia]]
    modId="bookcase"
    mandatory=true
    versionRange="[1.0,2.0)"
    ordering="NONE"
    side="SERVER"
```

[version_spec]: https://maven.apache.org/enforcer/enforcer-rules/versionRanges.html