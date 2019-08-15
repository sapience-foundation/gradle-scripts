Sapience Foundation - Gradle Scripts
==============

With `Gradle`, you can configure the current project to using an external build script. All of the Gradle build language is available in the external script. You can even apply other scripts from the external script.

With this repo, the idea is applies the given script to the current project. In other words, simple names occurring in the script (*e.g. path*) will be resolved using the project object.

To give an example, applying a script containing `println path` will print `project.path`.

`apply from:, to:` applies the given script to the object specified by `to:.` To give an example, applying a script containing `println path` to task will print `task.path`.
