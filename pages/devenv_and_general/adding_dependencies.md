### Adding Dependencies to your @Mod annotation

Adding Dependencies to your @Mod annotation is as simple as setting the dependencies field to this:
dependencies="required-after:forge@[minVersion,maxVersion)"

multiple dependencies are separated using ;, min and max version are optional. [, ] = included, (,) = excluded versions. you can also leave the min or max fields empty or omit the whole version range.
keywords
 after = load this mod after the one specified, if present
before = load this mod before the one specified, if present.

keywords can be prefixed with required-, which will force the specified modid to be present.

for more info on the version ranges see https://docs.oracle.com/middleware/1212/core/MAVEN/maven_version.htm#MAVEN402