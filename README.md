# Jenkins Artifactory Plugin Transitive groovy-all Dependency Fault demo
Demo for Maven build breaking through transitive groovy-all dependency in Jenkins Artifactory Plugin

[![Maven build status](https://github.com/lpradel/jenkins-artifactory-plugin-groovy-all-dependency-fault-demo/actions/workflows/maven.yml/badge.svg)](https://github.com/lpradel/jenkins-artifactory-plugin-groovy-all-dependency-fault-demo/actions/workflows/maven.yml)

In a minimal Maven / Java 8 project that has only a single `<dependency>` which is the Jenkins Artifactory Plugin like [in this demo](https://github.com/lpradel/jenkins-artifactory-plugin-groovy-all-dependency-fault-demo/blob/main/pom.xml#L25)
```
<dependency>
    <groupId>org.jenkins-ci.plugins</groupId>
    <artifactId>artifactory</artifactId>
    <version>4.0.8</version>
</dependency>
```

will result in breaking the Maven build because of the transitive dependency `org.codehaus.groovy:groovy-all:jar:3.0.13` which results from the dependency `org.jfrog.buildinfo:build-info-extractor-maven3`.

Resulting build error is:
```
Error:  Failed to execute goal on project jenkins-artifactory-plugin-groovy-all-dependency-fault-demo: Could not resolve dependencies for project com.lukaspradel:jenkins-artifactory-plugin-groovy-all-dependency-fault-demo:jar:1.0-SNAPSHOT: Could not find artifact org.codehaus.groovy:groovy-all:jar:3.0.13 in repo.jenkins-ci.org (https://repo.jenkins-ci.org/public/)
```
