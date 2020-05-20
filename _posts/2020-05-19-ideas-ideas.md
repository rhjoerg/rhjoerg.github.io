---
layout: post
title:  "Ideas, ideas, ..."
date:     2020-05-19
modified: 2020-05-19
categories: maven eclipse
excerpt: The number of ideas exceeds three. Time to write them down.
comments: true
---

The number of ideas exceeds three. Time to write them down.

### Automation of new project setup

I'm creating new repositories and therefore new Eclipse projects almost daily. Setting up the
files (`.project, .classpath, src/**`, etc) is a tedious and error-prone task.

Using the `New Project...` command in Eclipse results in a set of files that do not match my
preferences. All those files would have to be edited and adjusted. Again: tedious and error-prone.

As I know now how to fumble around with the GitHub repository (clone, modify, add, commit, push) using `jgit`
from within Java, I could write an application to automate this.

As an alternative I could write an Eclipse plugin.

### Using rhjoerg.github.io as Maven repository

As of now, I deploy the packages to GitHub. I will deploy them to `ossrh` once the projects have some maturity.

To access these packages, I need to declare the server in the `settings.xml`, giving a username and password
managed in the environment.

As I have to declare a separate server, I could as well declare `rhjoerg.github.io/maven` as a repository.

As a result, I would deploy the artifacts into some local repository, automatically download the
`rhjoerg.github.io` repository, add the artifacts into it and push the changes back to the site repository.

Or maybe the other way round: clone the `rhjoerg.github.io`, deploy into that repository, and push the changes.
This solution would probably require a helper Maven plugin.

### Testing compatibility to spring-starter-*

As I will write projects using Spring, I want my helper projects to be compatible with the `spring-starter-*`
projects. Compatibility here refers to versions of dependencies and plugins used.

I experimented with `org.codehaus.mojo:versions-maven-plugin:compare-dependencies`. I will have to inspect
their source code to see, whether this meets my requirements. The output created is not very reusable.
Maybe I still need my own Maven plugin to perform this.

### Local git server for testing

I am playing around with `jgit`. With every run I check out multiple GitHub repositories. To not bother
GitHub just because of a change of the format string of some `String.format` call. I need some local Git server.

### Further investigations into Jenkins

I'm still watching a three hour video about Jenkings. As Jenkins is written in Java, extensions for it
would be written in Java too. Let's see.

### Create images with Apache Batik

My site still has no `favicon.ico` and I want to have some graphics with embedded links. Some experiments
are required here.
