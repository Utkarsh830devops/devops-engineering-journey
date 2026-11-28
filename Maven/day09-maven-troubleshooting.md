# 🚀 Maven Day 9 - Troubleshooting & Real Production Build Failures

## Objective

Learn how to troubleshoot common Maven build issues in enterprise environments.

Topics Covered:

- Dependency Resolution Failure
- Corrupted Local Repository
- Java Version Mismatch
- Plugin Resolution Failure
- Unit Test Failures
- Snapshot vs Release
- Jenkins Build Troubleshooting
- Maven Debugging

---

# Why Troubleshooting Matters?

In real DevOps projects:

```text
Developer
   ↓
GitHub
   ↓
Jenkins
   ↓
Maven Build
   ↓
Deployment
```

Most production issues occur during:

```text
Build Stage
```

A DevOps Engineer must know how to diagnose and fix Maven failures quickly.

---

# Issue 1 - Dependency Resolution Failure

## Error

```text
Could not resolve dependencies
```

Examples:

```text
Failed to collect dependencies
```

```text
Could not find artifact
```

---

## Causes

- Invalid dependency version
- Wrong artifactId
- Repository unavailable
- Network issue
- Nexus unavailable

---

## Troubleshooting Commands

Show dependency tree:

```bash
mvn dependency:tree
```

Enable debug mode:

```bash
mvn clean install -X
```

---

## Example

Dependency:

```xml
<dependency>
    <groupId>com.company</groupId>
    <artifactId>sample-library</artifactId>
    <version>99.99.99</version>
</dependency>
```

Version does not exist.

Build fails.

---

# Issue 2 - Corrupted Local Repository

## Error

```text
ZipException
```

```text
Invalid CEN header
```

---

## Cause

Corrupted artifact inside:

```text
~/.m2/repository
```

---

## Fix

Delete specific dependency:

```bash
rm -rf ~/.m2/repository/org/springframework
```

or delete entire repository:

```bash
rm -rf ~/.m2/repository
```

Rebuild:

```bash
mvn clean install
```

---

# Issue 3 - Java Version Mismatch

## Error

```text
invalid target release
```

or

```text
Unsupported class file major version
```

---

## Cause

Project expects Java 17.

System has Java 11.

---

## Verification

```bash
java -version
```

```bash
mvn -version
```

---

## Fix

Update JAVA_HOME.

Verify:

Linux:

```bash
echo $JAVA_HOME
```
Windows:

```cmd
echo %JAVA_HOME%
```

---

# Issue 4 - Plugin Resolution Failure

## Error

```text
Plugin not found
```

Example:

```text
Failed to resolve plugin
```

---

## Causes

- Internet issue
- Proxy issue
- Repository unavailable
- Wrong plugin version

---

## Fix

Force update:

```bash
mvn clean install -U
```

Debug:

```bash
mvn -X
```

---

# Issue 5 - Unit Test Failure

## Error

```text
Tests Failed
```

Example:

```text
maven-surefire-plugin:test failed
```

---

## Verification

```bash
mvn test
```

Reports generated at:

```text
target/surefire-reports
```

---

## Temporary Troubleshooting

Skip Tests:

```bash
mvn clean package -DskipTests
```

⚠ Only for troubleshooting, not for production deployment.

---

# Issue 6 - Snapshot vs Release

## Snapshot Version

```text
1.0.0-SNAPSHOT
```

Meaning:

```text
Development Version
```

Changes frequently.

---

## Release Version

```text
1.0.0
```

Meaning:

```text
Stable Production Version
```

---

# Comparison

| Snapshot | Release |
|----------|----------|
| Mutable | Immutable |
| Development | Production |
| Frequently Updated | Stable |

---

# Issue 7 - Build Hangs

## Symptoms

```text
Maven build never completes
```

---

## Possible Causes

- Proxy issue
- DNS issue
- Internet issue
- Nexus outage

---

## Troubleshooting

```bash
mvn -X

```text
Downloading...
```

stuck messages.

---

# Issue 8 - Jenkins Build Fails But Local Works

## Example

Local:

```text
SUCCESS
```

Jenkins:

```text
FAILED
```

---

## Possible Causes

- Different Java version
- Different Maven version
- Missing environment variables
- Repository access issue
- Network restrictions

---

## Verification

Check Jenkins Agent:

```bash
java -version
```

```bash
mvn -version
```

Compare with local machine.

---

# Important Debug Commands

## Show Maven Version

```bash
mvn -version
```

---

## View Dependency Tree

```bash
mvn dependency:tree
```

---

## Enable Debug Logging
```bash
mvn -X
```

---

## Force Dependency Refresh

```bash
mvn clean install -U
```

---

## Show Effective POM

```bash
mvn help:effective-pom
```

---

# Real Jenkins Troubleshooting Flow

```text
Build Failed
    ↓
Check Jenkins Console Logs
    ↓
Check Java Version
    ↓
Check Maven Version
    ↓
Check Dependency Resolution
    ↓
Check Plugins
    ↓
Check Nexus Access
    ↓
Run Maven in Debug Mode
```

---

# Portfolio Management Platform Scenario

## Incident

Portfolio Service build failed.

Error:

```text
Could not resolve dependency
```

---

## Investigation

```bash
mvn dependency:tree
```

```bash
mvn -X
```

---

## Root Cause

```text
Nexus repository unavailable
```

---

## Resolution

Restore Nexus connectivity.

Re-run:

```bash
mvn clean install
```

Build successful.

---

# Interview Questions

## Jenkins build fails. What is your first step?

Answer:

```text
Check Jenkins console logs.
```

---

## What does mvn -X do?

Enables detailed Maven debug logging.

---

## How do you fix corrupted dependencies?

```bash
rm -rf ~/.m2/repository

mvn clean install
```

---

## Difference Between Snapshot and Release?

Snapshot:

```text
Development Version
```

Release:

```text
Production Ready Stable Version
```

---

## Local Build Works But Jenkins Fails. What Do You Check?

- Java Version
- Maven Version
- Environment Variables
- Repository Connectivity
- Network Access

---

# Hands-On Commands

```bash
mvn -version
```

```bash
mvn dependency:tree
```

```bash
mvn help:effective-pom
```

```bash
mvn clean install -U
```

```bash
mvn -X validate
```

---

# Key Learnings

✅ Dependency failures are the most common Maven issues

✅ .m2 repository corruption can break builds

✅ Java version mismatches frequently occur in Jenkins

✅ Plugin issues can be diagnosed with debug mode

✅ Snapshot and Release versions behave differently

✅ Jenkins troubleshooting starts with console logs

✅ mvn -X is one of the most important debugging commands

---

# Commands to Remember

```bash
mvn -version

mvn dependency:tree

mvn help:effective-pom

mvn clean install -U

mvn test

mvn -X
```

---

## Status

✅ Completed
