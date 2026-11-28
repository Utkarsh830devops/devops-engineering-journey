# 🚀 Maven Day 5 - Parent POM & Multi-Module Maven Projects

## Objective

Learn how enterprise applications manage multiple microservices using a Parent POM and Multi-Module Maven architecture.

---

# Problem Statement

Portfolio Management Platform contains multiple services:

```text
Portfolio Service
Trade Service
Client Service
Risk Engine
```

Without a Parent POM:

```text
Each service manages:

Dependencies
Plugins
Java Version
Build Configuration
```

This becomes difficult to maintain.

---

# Solution

Use a Parent POM.

```text
portfolio-management-platform
│
├── pom.xml (Parent POM)
│
├── portfolio-service
├── trade-service
├── client-service
└── risk-engine
```

---

# What is a Parent POM?

A Parent POM is a central Maven configuration file shared by all modules.

Benefits:

- Common Dependencies
- Common Plugins
- Common Java Version
- Centralized Management

---

│
├── trade-service
│   └── pom.xml
│
├── client-service
│   └── pom.xml
│
└── risk-engine
    └── pom.xml
```

---

# Parent POM Example

Location:

```text
portfolio-management-platform/pom.xml
```

```xml
<project>

    <modelVersion>4.0.0</modelVersion>

    <groupId>com.utkarsh.portfolio</groupId>

    <artifactId>portfolio-management-platform</artifactId>

    <version>1.0.0</version>

    <packaging>pom</packaging>

</project>
```

---

# Why Packaging = pom?

Parent projects do not generate:

```text
JAR
WAR
```

Parent project only manages:

```text
Modules
Dependencies
Plugins
Versioning
```

Therefore:

```xml
<packaging>pom</packaging>
```

---

# Defining Modules

Inside parent POM:

```xml
<modules>

<module>portfolio-service</module>

    <module>trade-service</module>

    <module>client-service</module>

    <module>risk-engine</module>

</modules>
```

---

# Parent POM Structure

```xml
<project>

    <groupId>com.utkarsh.portfolio</groupId>

    <artifactId>portfolio-management-platform</artifactId>

    <version>1.0.0</version>

    <packaging>pom</packaging>

    <modules>

        <module>portfolio-service</module>
        <module>trade-service</module>
        <module>client-service</module>
        <module>risk-engine</module>

    </modules>

</project>
```

---

# Child POM Example

Portfolio Service:

```xml
<project>

    <parent>

        <groupId>com.utkarsh.portfolio</groupId>

        <artifactId>portfolio-management-platform</artifactId>

        <version>1.0.0</version>

    </parent>

    <artifactId>portfolio-service</artifactId>

</project>
```

---

# Benefit of Parent POM

Instead of repeating:

```xml
Java Version
Spring Boot Version
JUnit Version
```

in every project,

we define once:

```xml
Property
Dependency
Plugin
```

inside Parent POM.

---

# Dependency Management

Parent POM:

```xml
<dependencyManagement>

</dependencyManagement>
```

Purpose:

```text
Control dependency versions centrally.
```

Example:

```xml
<dependencyManagement>

    <dependencies>

        <dependency>

            <groupId>org.springframework.boot</groupId>

            <artifactId>spring-boot-starter-web</artifactId>

            <version>3.5.0</version>

        </dependency>

    </dependencies>

</dependencyManagement>
```

---

trade-service
risk-engine
```

individually,

build everything:

```bash
mvn clean install
```

from parent directory.

---

# Build Flow

```text
Parent POM
      ↓
Portfolio Service
      ↓
Trade Service
      ↓
Client Service
      ↓
Risk Engine
```

---

# Real Enterprise Example

Portfolio Management Platform:

```text
portfolio-service

trade-service

client-service

risk-engine
```

Build command:

```bash
mvn clean install
```

Output:

```text
portfolio-service.jar

trade-service.jar

client-service.jar

risk-engine.jar
```

Generated together.

---

# Jenkins Integration

Pipeline:

```groovy
stage('Build') {

    steps {

        sh 'mvn clean install'

    }

}
```

Result:

```text
All modules built together.
```

---

# Directory Structure

```text
portfolio-management-platform

│
├── pom.xml
│
├── portfolio-service
│   └── pom.xml
│
├── trade-service
│   └── pom.xml
│
├── client-service
│   └── pom.xml
│
└── risk-engine
    └── pom.xml
```

---

# Common Commands

## Validate Entire Platform

```bash
mvn validate
```

---

## Build Entire Platform

```bash
mvn clean install
```

---

## Build Specific Module

```bash
mvn -pl portfolio-service install
```

---

## Build Module With Dependencies

```bash
mvn -pl portfolio-service -am install
```

---

# Interview Questions

## What is a Parent POM?

A Parent POM is a centralized Maven configuration shared across multiple modules.

---

## Why use a Parent POM?

- Consistent versions
- Centralized dependencies
- Shared plugins
- Easier maintenance

---

## What is a Multi-Module Project?

A Maven project that contains multiple modules managed by a Parent POM.

---

## Why is packaging set to pom?

Because Parent POMs do not generate JAR or WAR artifacts.

---

## What is dependencyManagement?

A section used to centrally manage dependency versions across modules.

---

## Difference between dependencies and dependencyManagement?

### dependencies

Immediately adds dependencies.

### dependencyManagement

Only manages versions and configuration.

---

## What command builds all modules?

```bash
mvn clean install
```

---

# Real DevOps Workflow

GitHub
↓
Jenkins
↓
Parent POM
↓
Build All Services
↓
Generate JARs
↓
Docker Build
↓
Container Registry
↓
Kubernetes Deployment

---

# Key Learnings

✅ Parent POM centralizes configuration

✅ Multi-Module Maven projects support microservices

✅ dependencyManagement controls versions

✅ pluginManagement controls plugins

✅ Packaging type for Parent POM is pom

✅ mvn clean install builds all modules

✅ Enterprise projects commonly use Parent POM architecture

---

## Status

✅ Completed
