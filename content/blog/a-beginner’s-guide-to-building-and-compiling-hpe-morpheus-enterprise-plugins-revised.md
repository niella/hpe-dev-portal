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

## JDK Prerequisite

The demonstration lab used for this article is based on a ***Windows 11 host*** with internet access and ***Visual Studio Code*** installed.

The lab also uses an ***HPE Morpheus Enterprise*** 8.0.10 ***appliance***. Generally, HPE Morpheus Enterprise endeavors to maintain backward compatibility, so slightly newer or older version will work as well.

The environment also needs to have Java ***JDK 11*** or ***17*** installed. The vendor distribution of Java is not critical — both OpenJDK and Oracle JDK are supported.

When using JDK 17, the project’s compile ***compatibility level is set to version 1.11*** to maintain compatibility with earlier environments.

To install the OpenJDK 17 distribution via the Microsoft Store, open a Windows command prompt (Press Win + R or click Start, type cmd, press enter), then run the following install command:

`winget install jdkbuild.openjdk.17.jdk`

To verify the OpenJDK install, run:

`java -version`

![](/img/install_java.png)



