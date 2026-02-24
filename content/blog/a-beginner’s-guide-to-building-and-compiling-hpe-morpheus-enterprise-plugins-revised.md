---
title: A Beginner’s Guide to Building and Compiling HPE Morpheus Enterprise
  Plugins Revised
date: 2026-02-23T07:59:18.548Z
author: Neil van Rensburg
authorimage: /img/greenlogo.png
disable: false
---
![]()

## Introduction

HPE Morpheus Enterprise is a hybrid cloud platform that unifies diverse products and technologies into a consistent workload-lifecycle orchestration, governance, and control framework.

This makes HPE Morpheus Enterprise ideally positioned to integrate with a broad ecosystem of cloud-related service vendors. These integrations are enabled through technology-specific plugin providers. HPE Morpheus Enterprise is extendable with custom plugins for clouds, task types, UI tabs, reports, approvals, cypher, IPAM, backups and more.

This article covers the process of generating and compiling a basic HPE Morpheus Enterprise generic plugin project on Windows 11. To understand how the workflow fits together, this blog will cover:

* Generating a new project using the plugin code generator
* Unzipping and opening the project in an IDE
* Exploring main plugin file components
* Compiling the plugin on Windows
* Uploading the compiled plugin to HPE Morpheus Enterprise
* Compiling the plugin remotely on Linux, using Visual Studio Code
* Compiling the plugin using Docker

## JDK & demo lab prerequisites

The demonstration lab used for this article is based on a ***Windows 11 host*** with internet access and ***Visual Studio Code*** installed.

The lab also uses an ***HPE Morpheus Enterprise*** 8.0.10 ***appliance***. Generally, HPE Morpheus Enterprise endeavors to maintain backward compatibility, so slightly newer or older version will work as well.

The environment also needs to have Java ***JDK 11*** or ***17*** installed. The vendor distribution of Java is not critical — both OpenJDK and Oracle JDK are supported.

When using JDK 17, the project’s compile ***compatibility level is set to version 1.11*** to maintain compatibility with earlier environments.

To install the OpenJDK 17 distribution via the Microsoft Store, open a Windows command prompt (Press Win + R or click Start, type cmd, press enter), then run the following install command:

```bash
winget install jdkbuild.openjdk.17.jdk
```

To verify the OpenJDK install, run:

```bash
java -version
```

![](/img/install_java.png)

## Creating a plugin project

Creating a project that compiles code into usable plugins can be a daunting task, especially for developers who are not familiar with Java, Groovy, or Gradle.

To simplify this process and make it easier for potential plugin builders to get started, the HPE Morpheus Enterprise engineering team created the Plugin Code Generator. The ["Getting Started" section of the HPE Morpheus Enterprise Developer Documentation](https://developer.morpheusdata.com/docs#_getting-started) has a comprehensive section on how to construct a plugin project.

This article uses the Plugin Code Generator tool. Using a web browser, navigate to <https://developer.morpheusdata.com/>. Click the ***GET STARTED NOW*** button:

![Morpheus Developer Site](/img/developer_site.png)

Use the following field values for this demo example:

- - -

|                       |                     |
| --------------------- | ------------------- |
| **Name:**             | Plugin Demo         |
| **Code:**             | pluginDemo          |
| **Morpheus Version:** | 8.0.X               |
| **Language:**         | Groovy              |
| **Base Package:**     | com.example         |
| **Providers:**        | Generic Integration |

- - -

![Generate Plugin Project](/img/generate_plugin.png)

Unzip the plugin project for use in an IDE. For this example, we will unzip the plugin to the Windows Documents folder:

![Extracted Plugin Project](/img/plugin_extracted.png)

## Authoring plugin projects in an IDE

Adding logic and complexity to a working plugin is an exercise in object-oriented programming. Writing code in plain text editors can be tedious, time-consuming, and error prone. To make development easier, use an IDE such as Visual Studio Code.



Although this simple demo example uses Visual Studio Code, several more powerful Java/Groovy IDEs are available, including products like IntelliJ IDEA, Eclipse, and NetBeans.

Open ***Visual Studio Code*** and select ***Open Folder*** from the ***File*** menu:
