# Forge gradle stuff

[Forge's docs][forgedocs] say to set the `archivesBaseName`, `group`, and
`version` fields in `build.gradle`, but they don't really give any explanation
as to what they do.  The code compiles fine even with archivesBaseName and group
set to different values from what the actual package name is, and in fact the
forge template doesn't even have the package name consistent with those. Turns
out gradle just compiles everything in the src/ directory by default,[^grlayout]
so your package name and `archivesBaseName` don't necessarily need to be the
same.  However, [Gradle's docs][grdocs] mention `archivesBaseName` and
`version`. These are what determine the name of the jar file gradle generates.
For example, the default value of `archivesBaseName` is `modid`, and the default
value of `version` is `1.0`. So the generated jar file is called
`modid-1.0.jar`.

I couldn't find any info on what `group` does. It doesn't seem to affect the
compilation of anything, and gradle doesn't seem to have any documentation on
it. You may be able to get away with not setting it, but it also probably isn't
a bad idea to set it to your package name. It might be something ForgeGradle
uses. (ForgeGradle is a plugin for gradle to build forge mods).


[forgedocs]: https://mcforge.readthedocs.io/en/latest/gettingstarted/#simple-buildgradle-customizations
[^grlayout]: https://docs.gradle.org/current/userguide/java_plugin.html#sec:java_project_layout
[grdocs]: https://docs.gradle.org/current/userguide/java_plugin.html
