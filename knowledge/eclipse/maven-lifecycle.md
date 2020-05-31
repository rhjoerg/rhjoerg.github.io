---
layout: page
title: "Maven Lifecycle"
date:     2020-05-20
modified: 2020-05-20
---

I am always googling for [Maven Lifecycle][maven-lifecycle]. I now use this cheat-sheet.

Maven defines the [Default Bindings][default-bindings].

### Clean Lifecycle

| Phase | Goal | Plugin |
| --- | --- | --- |
| `pre-clean` | no default goal ||
| `clean` | `clean:clean` | [Clean][maven-clean-plugin] |
| `post-clean` | no default goal ||

### Default Lifecycle

| Phase | Goal | Plugin | Remarks |
| --- | --- | --- | --- |
| `validate` ||||
| *tbd* ||||
| `process-resources` | `resources:resources` | [Resources][maven-resources-plugin] | `jar` |
| *tbd* ||||
| `package` | `jar:jar` | [Jar][maven-jar-plugin] | `jar` |
| *tbd* ||||

[maven-lifecycle]: http://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html
[default-bindings]: http://maven.apache.org/ref/3.6.3/maven-core/default-bindings.html

[maven-clean-plugin]: https://maven.apache.org/plugins/maven-clean-plugin/
[maven-resources-plugin]: https://maven.apache.org/plugins/maven-resources-plugin/
[maven-jar-plugin]: https://maven.apache.org/plugins/maven-jar-plugin/
