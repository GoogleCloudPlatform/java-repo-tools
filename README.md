# Google Cloud Platform repository tools for Java®

[![Build
Status](https://travis-ci.org/GoogleCloudPlatform/java-repo-tools.svg?branch=master)](https://travis-ci.org/GoogleCloudPlatform/java-repo-tools) [![Maven](https://maven-badges.herokuapp.com/maven-central/com.google.cloud.samples/shared-configuration/badge.svg)
](http://search.maven.org/#search%7Cga%7C1%7Ccom.google.cloud.samples) [![Coverage
Status](https://codecov.io/gh/GoogleCloudPlatform/java-repo-tools/branch/master/graph/badge.svg)](https://codecov.io/gh/GoogleCloudPlatform/java-repo-tools)

This is a collection of common tools used to maintain and test Java repositories
in the [GoogleCloudPlatform](https://github.com/GoogleCloudPlatform)
organization.


## Using this repository

This package is meant to be used as a parent pom, so that [CheckStyle](https://github.com/checkstyle/checkstyle), [ErrorProne](http://errorprone.info/) and other plugins run against sample code. Please ensure that samples function without this parent definition. The parent should be used only to enforce style and other checks.

```xml
    <!--
      The parent pom defines common style checks and testing strategies for our samples.
      Removing or replacing it should not affect the execution of the samples in anyway.
    -->
    <parent>
        <groupId>com.google.cloud.samples</groupId>
        <artifactId>shared-configuration</artifactId>
        <version>1.0.12</version>
    </parent>
```

You must also copy the files `google-checks.xml` and `suppressions.xml` to the same directory for the parent to work. We are working on [removing this requirement](https://github.com/GoogleCloudPlatform/java-repo-tools/issues/41).

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
