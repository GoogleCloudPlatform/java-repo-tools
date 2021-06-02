# Google Cloud Platform repository tools for Java®

[![Maven](https://maven-badges.herokuapp.com/maven-central/com.google.cloud.samples/shared-configuration/badge.svg)
](http://search.maven.org/#search%7Cga%7C1%7Ccom.google.cloud.samples) 

This is a collection of common tools used to maintain and test Java repositories
in the [GoogleCloudPlatform](https://github.com/GoogleCloudPlatform)
organization.


## Using this repository

This package should be used as a parent `pom.xml`. It adds:
 * [CheckStyle](https://github.com/checkstyle/checkstyle) Enforces the 
 [Google Java Style guide](https://google.github.io/styleguide/javaguide.html)
 * [ErrorProne](http://errorprone.info/) Google written code analyzer
 * [PMD](https://pmd.github.io/) A cross-language static code analyzer
 * [SpotBugs](https://spotbugs.readthedocs.io/en/stable/) Find well know bug patterns with these
 extensions:
   * [Find Security Bugs](http://find-sec-bugs.github.io/) Security audits of Java Web Applications.
   * [fb-contrib](http://fb-contrib.sourceforge.net/) Static code analysis on Java byte code.

Please ensure that samples function without this parent definition.

```xml
    <!--
      The parent pom defines common style checks and testing strategies for our samples.
      Removing or replacing it should not affect the execution of the samples in anyway.
    -->
    <parent>
        <groupId>com.google.cloud.samples</groupId>
        <artifactId>shared-configuration</artifactId>
        <version>1.0.19</version>
    </parent>
```

## USAGE

```bash
mvn -P lint clean verify
```

## Where is this used?

This package should be used for all Google Cloud Platform samples for Java. This includes,

- [Google Cloud Platform samples](https://github.com/GoogleCloudPlatform/java-docs-samples)
- [Getting started on Google Cloud Platform](https://github.com/GoogleCloudPlatform/getting-started-java)
- [Getting started wtih App Engine](https://github.com/GoogleCloudPlatform/appengine-try-java)
- [Cloud Bigtable samples](https://github.com/GoogleCloudPlatform/cloud-bigtable-examples/tree/master/java)


## Contributing changes

-  See [CONTRIBUTING.md](CONTRIBUTING.md)


## Licensing

- Apache 2.0 - See [LICENSE](LICENSE)

Java is a registered trademark of Oracle Corporation and/or its affiliates.
