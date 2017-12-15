# Releasing

In general, follow the [instructions at Sonatype for using the Maven release
plugin](http://central.sonatype.org/pages/apache-maven.html).

## Release the checkstyle-config package

NOTE - Need to clean up instructions below, but the following works, after fixing the version (for
all 3 pom.xml's), updating GH, tagging the release:

    cd checkstyle-config
    mvn clean verify deploy -P release
    cd ..
    mvn clean verify deploy -P release

That will open, upload, close, and release.  The parent will need you to visit sonatype to close,
and verify manually.

### Not yet updated to old way

First, release the checkstyle-config package.

    cd checkstyle-config
    mvn release:clean release:prepare

This creates commits for the release and tags it. Next, update the parent pom
to use the latest snapshot version so that the tests continue to pass.

    # Update the version in the checkstyle plugin resource dependencies.
    vim ../pom.xml
    git add ../pom.xml
    git commit
    git push origin branchname

Then, make a pull request for the release. After verifying that it works,
perform the release to upload it to Maven Central.

    mvn release:perform

## Release the shared-configuration package

After releasing the checkstyle-config package (if needed), update the root `pom.xml` to
depend on the released version and push & publish to Github.

<!--
    # Use the latest released version of checkstyle-config.
    vim pom.xml
    git add pom.xml
    git commit
 -->


Next, prepare a release.

1. sync to head; create a new branch
1. remove `-SNAPSHOT` in both `pom.xml` and `test/pom.xml`
1. Commit & Push to Github
1. Merge on Github
1. Tag the release on Github
1. pull MASTER
1. `mvn clean deploy -P release`
1. At Maven Central close the release and release.
1. On a new branch
1. Increment the version number and add `-SNAPSHOT` in `pom.xml`, `test/pom.xml`, and if required
`checkstyle-config/pom.xml`.
1. Commit & Push to Github
1. Merge on Github

<!--
    mvn release:clean release:prepare

Next, update the version of the parent in `test/pom.xml`. Also update `pom.xml`
to use the latest snapshot of checkstyle-config.

Then, make a pull request for the release. After verifying that it works,
perform the release to upload it to Maven Central.

    mvn release:perform
 -->

A copy of my `.m2/settings.xml`:
```xml
<settings>
  <servers>
    <server>
      <id>ossrh</id>
      <username>XXXXXX</username>
      <password>YYYYYYYYYYYYYYYYYYYY</password>
    </server>
    <server>
      <id>ZZZZZZZZ</id>
      <passphrase></passphrase>
    </server>
  </servers>
  <profiles>
    <profile>
      <activation>
        <activeByDefault>true</activeByDefault>
      </activation>
      <properties>
        <gpg.keyname>ZZZZZZZZ</gpg.keyname>
      </properties>
    </profile>
  </profiles>
</settings>
```
