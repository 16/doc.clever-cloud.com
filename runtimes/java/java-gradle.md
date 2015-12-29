---
title: Gradle deployment
position: 3
shortdesc: Gradle is a project automation tool that builds…
tags:
- java
---

# Deploy Gradle projects

Clever Cloud offers you to run your Gradle projects. You can deploy this kind of project
without changing your code, but running it on Clever Cloud needs some configuration files,
to add parameters like your gradle task for example.

## Overview

Gradle is a project automation tool that builds upon the concepts of
Apache Ant and Apache Maven and introduces a Groovy-based
domain-specific language (DSL) instead of the more traditional XML form
of declaring the project configuration.

## Create an application

Refer to the page [Deploy an application on Clever Cloud](/doc/clever-cloud-overview/add-application/).

## Necessary information

You *must* provide a `clevercloud/gradle.json` file (gradle.json file in
clevercloud folder which is at the root of you application) that
contains at least the following:

```javascript
{
    "deploy": {
        "goal": "grails:run"
    }
}
```

That is the only option you really need to supply.

## Optional configuration

The full configuration can look like the following:

```haskell
{
  "build": {
    "type": "<string>",
    "goal": "<string>"
  },
  "deploy": {
    "goal": "<string>"
  },
  "hooks": {
     "postDeploy": "<string>"
  }
}
```
You can use the following properties:

* ``build``
    * ``"type"`` can be ``"maven"``, ``"gradle"`` or ``"ant"``.
    * ``"goal"`` is the target you want to use to build your project.
* ``deploy``
    * ``"goal"`` the goal/target and options you want to execute to
		  deploy/run you project. (This one is mandatory.)
* ``hooks``
    * ``postDeploy`` execute a custom script after the deployment. Some frameworks or custom applications might require bootstrapping before the application may run.
You can achieve this by creating a custom script with your commands and adding the associated file name.

## The Gradle Wrapper

Since Gradle can come in many versions, Clever Cloud automatically support the
[Gradle Wrapper|http://www.gradle.org/docs/current/userguide/gradle_wrapper.html]:
Just create and commit the `gradlew` file and the wrapper `jar` and
`properties` files:

```haskell
./
	clevercloud/
		gradle.json
	gradlew
	gradle/wrapper/
		gradle-wrapper.jar
		gradle-wrapper.properties
	src/
```


## Environment injection

Clever Cloud can inject environment variables that are defined in the
dashboard and by add-ons linked to your application.

For Java applications, the environment is injected in the
`System.getProperties()` object. So, to use a variable, you just do
`System.getProperties().getProperty("MY_VARIABLE")`.

For Groovy applications, just use the `System.getProperty("MY_VARIABLE")`.

