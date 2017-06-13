Java 9 vs Gradle
================

This is a demo repository for a post on my blog that shows how to run Gradle build on JDK9. As a bonus, I show the current
state of Jigsaw.

What works
----------

After some extra setup of Gradle, it is possible to build `jdk9-sample` with the standard command:

```bash
# gradle build publishToMavenLocal
```

It is not possible to build `jdk9-application` which uses the module defined by the first project. The reason is that Gradle apparently does not add necessary parameters that configure the path to the JAR with the module. I do not attempt to workaround it, because it would require hard-coding the path to the local Maven repository or whatever Gradle does. I think this is a waste of time and that we should better wait for at least a minimal support in Gradle.

Necessary Gradle setup
----------------------

The following environment variable must be set:

```
GRADLE_OPTS=--add-opens java.base/java.lang=ALL-UNNAMED
```

Add the following line to `gradle.properties`:

```
org.gradle.daemon=false
```

The code is available as a public domain. Regards and waiting for the official support!
