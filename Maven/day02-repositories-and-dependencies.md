# Maven Day 2

## Repository Types

### Local Repository

~/.m2/repository

### Central Repository

repo.maven.apache.org

### Remote Repository

- Nexus
- Artifactory

## Important Commands

```bash
mvn validate

mvn dependency:resolve

mvn dependency:tree
```

## Dependency Flow

pom.xml
↓
Maven
↓
Local Repository
↓
Maven Central
↓
Download Dependency

## Key Learnings

- Maven uses repositories to manage dependencies.
- Dependencies are stored in .m2 repository.
- Maven Central is the default public repository.
- dependency:tree helps troubleshoot dependency issues.
