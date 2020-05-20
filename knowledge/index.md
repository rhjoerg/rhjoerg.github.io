---
layout: page
title: "Knowledge"
date:     2020-05-15
modified: 2020-05-20
---

## Eclipse / Maven

- How to set maven properties via [Eclipse runtime configuration][eclipse-runtime-configuration].
- The [Maven Lifecycle][maven-lifecycle].
- How to [create an Eclipse Plugin with Eclipse and Maven][create-eclipse-plugin-with-eclipse-and-maven]

## Page Editing

Documentation for the "minima" theme found at [Minima's GitHub Repository][minima-repo].

Footnotes in markdown files must not have a space in front of the colon.

## CI on GitHub (I no longer use this)

To setup this CI, an additional [file](https://github.com/rhjoerg/rhj-java-dependencies/blob/master/.github/workflows/build.yml) is required.
Editing this file can be done within the GitHub site as it supports auto-completion.

This [action][github-action] may be helpful to fetch common components.

[eclipse-runtime-configuration]: eclipse/how-to-set-maven-properties-in-eclipse-runtime-configuration.html
[maven-lifecycle]: eclipse/maven-lifecycle.html
[create-eclipse-plugin-with-eclipse-and-maven]: eclipse/create-eclipse-plugin-with-eclipse-and-maven.html
[github-action]: https://github.com/actions/checkout#Checkout-multiple-repos-side-by-side
[minima-repo]: https://github.com/jekyll/minima