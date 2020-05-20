---
layout: page
title: "Create Maven Plugin with Eclipse and Maven"
date:     2020-05-20
modified: 2020-05-20
---

This is work in progress. See [rhj-eclipse-tools][rhj-eclipse-tools] as it progresses.

Contents:
- [Eclipse Project Setup](#phase-1-eclipse-project-setup)
- [Maven Setup](#phase-2-maven-setup)

## Phase 1: Eclipse Project Setup

- Setup your project as a maven project.
- Add a `build.properties` file.
- Adjust the `.classpath` file.
- Create the `MANIFEST.MF` file.
- Create the `plugin.xml` file.
- Adjust the `.project` file.

### The `build.properties` file

```
custom = true

source = src/main/java/, src/main/resources/
output = target/classes/

bin.includes = plugin.xml
```

- Make sure to adjust the `source` to point to your maven sources and not to the default `source..=src/` if created with `New Project...`.
- Make sure to set the correct `output`

### The `.classpath` file

The `.classpath` file of a Maven project is rather complex. Just add the line

```xml
<classpathentry kind="con" path="org.eclipse.pde.core.requiredPlugins"/>
```

where you see the other `<classpathentry kind="con" .../>` entries.

### The `MANIFEST.MF` file

This file needs to be placed into the folder `META-INF` at the root of the project, as Eclipse happily ignores a `manifest=`
setting in the `build.properties` file.

As a result, this file is not included in the final `.jar`. This is [resolved later](#manifestmf).

### The `plugin.xml` file

It can be as empty as:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<?eclipse version="4.15"?>
<plugin>
</plugin>
```

Although this provokes an Eclipse warning. This warning can be ignored for now.

### The `.project` file

Add the plugin builders and nature as seen in the [`.project` file][rhj-eclipse-tools-project].

## Phase 2: Maven Setup

Of course, Maven doesn't know about the *Plug-in Dependencies* of the eclipse project.
The dependencies have to be included in the `pom.xml` file.

The required components are available in the `central` repository.

### Dependencies

The `org.eclipse.swt` artifact doesn't have a valid POM. Therefore it needs to be excluded for now.
See the `dependencyManagement` section in the [`pom.xml` file][rhj-eclipse-tools-pom] of the referenced project.
**I don't know (yet) how to get access to the `SWT` class used for UI**.

To start of, the following dependencies suffice:

```xml
<dependencies>
  <dependency>
    <groupId>org.eclipse.platform</groupId>
    <artifactId>org.eclipse.ui</artifactId>
  </dependency>
</dependencies>
```

### MANIFEST.MF

The generated `.jar` file needs to have the correct `MANIFEST.MF`. This is achieved by adding the following
section to the `pom.xml`:

```xml
<pluginManagement>
  <plugins>
    <plugin>
      <artifactId>maven-jar-plugin</artifactId>
      <configuration>
        <archive>
          <manifestFile>META-INF/MANIFEST.MF</manifestFile>
        </archive>
      </configuration>
    </plugin>
  </plugins>
</pluginManagement>
```


[rhj-eclipse-tools]: https://github.com/rhjoerg/rhj-eclipse-tools
[rhj-eclipse-tools-project]: https://github.com/rhjoerg/rhj-eclipse-tools/blob/master/.project
[rhj-eclipse-tools-pom]: https://github.com/rhjoerg/rhj-eclipse-tools/blob/master/pom.xml

