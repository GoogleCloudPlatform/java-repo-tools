# Releasing

In general, follow the [instructions at Sonatype for using the Maven release
plugin](http://central.sonatype.org/pages/apache-maven.html).

## Update Versions

Remove the `-SNAPSHOT` from the versions property in the following POMs:
* pom.xml (3 of them)
* checkstyle-config/pom.xml (one)
* test/pom.xml (one)

PR changes to master, and once accepted use `git pull` update the master branch locally.

Don't forget to specify a release tag on Github once your PR is accepted.

## Release Packages

From the root project folder, run the following command to release `checkstyle-config`:

    cd checkstyle-config
    mvn -P release clean verify deploy 
    mvn -P release deploy 

Next, use the following to release `shared-configuration`:

    cd ..
    mvn -P release clean verify 
    mvn -P release deploy 

That will open, upload, close, and release.  The parent will need you to visit sonatype to close,
and verify manually.


## Prepare for Next Release

Increment the version number, and append `-SNAPSHOT` (ie. '1.0.10' becomes '1.0.11-SNAPSHOT') inside the following POMs:

Add the `-SNAPSHOT` from the versions property in the following POMs:
* pom.xml (3 places)
* checkstyle-config/pom.xml (1 place)
* test/pom.xml (1 place)

PR changes to master.

## .m2 Settings
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
