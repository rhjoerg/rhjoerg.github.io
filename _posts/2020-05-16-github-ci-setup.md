---
layout: post
title:  "GitHub CI/CD setup"
date:     2020-05-16
modified: 2020-05-16
categories: github ci
---

After reading multiple online documents to setup the CI/CD, I now have a running solution.

Important: Each repository needs its own set of secrets!

But I have now a [maven repository](https://github.com/rhjoerg/maven) containing the first few packages automatically deployed
by their respective configuration. See the [rhj-java-dependencies repository](https://github.com/rhjoerg/rhj-java-dependencies) as an example.

There are three important files:
- the [`build.yml`][workflow] configuration (must not be named like that)
- the [`settings.xml`][settings] file
- the [`pom.xml`][pom]'s `distributionManagement` section.

The ids whithin the `settings.xml` (server id, profile id, ...) and within the `pom.xml` must match!

Now I have to manage multiple `settings.xml`s and `build.yml`s. Let's see, how to automate this.

### Lessons Learned

#### Do not follow blindly to what is written in documents

I found some documentation telling me, how to use a custom `settings.xml` within the CI. In the example given, there was a line to
auto-configure the `settings.xml` file. I happily followed the order (see lines 26 and 27 of an
[older version][workflow-diff] of my `build.yml`). Given these lines, GitHub CI happily replaced my `settings.xml` with its own interpretation
of the situation.

#### Access restrictions of GitHub CI

The `GITHUB_TOKEN` automatically set by GitHub CI doesn't have access to repositories outside of the 'running' repository. This works well for a
build, but fails to deploy to my `maven` repository. Therefore a global token needs to be created, added to each repository's secrets and then
used within the build (see the `env` entry in the [workflow][workflow] file).

#### Access restriction to published packages

As of [this answer][answer], you need to authenticate to use the public (sic!) packages as dependencies in your projects. As of 2020-05-01 this hasn't
changed yet.

[answer]: https://github.community/t5/GitHub-API-Development-and/Download-from-Github-Package-Registry-without-authentication/m-p/35501#M3312
[pom]: https://github.com/rhjoerg/rhj-java-dependencies/blob/master/pom.xml
[settings]: https://github.com/rhjoerg/rhj-java-dependencies/blob/master/settings.xml
[workflow]: https://github.com/rhjoerg/rhj-java-dependencies/blob/master/.github/workflows/build.yml
[workflow-diff]: https://github.com/rhjoerg/rhj-java-dependencies/commit/bb97534657c03e125b17b73fb931ad425204ca8e#diff-898e737ee4e56ba042bda31764bed49e
