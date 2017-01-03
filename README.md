Provide various parent pom.xml for contrib extensions.

Extensions are automatically release on http://nexus.xwiki.org if your user have the release right.

# Example

For extensions having xwiki-platform dependencies:

```xml
  <parent>
    <groupId>org.xwiki.contrib</groupId>
    <artifactId>parent-platform</artifactId>
    <version>6.4-5</version>
  </parent>
```

For extensions having xwiki-rendering and xwiki-commons dependencies:

```xml
  <parent>
    <groupId>org.xwiki.contrib</groupId>
    <artifactId>parent-rendering</artifactId>
    <version>6.4-5</version>
  </parent>
```

For extensions having xwiki-commons dependencies only:

```xml
  <parent>
    <groupId>org.xwiki.contrib</groupId>
    <artifactId>parent-commons</artifactId>
    <version>6.4-5</version>
  </parent>
```

# Versions

Version is \<branch>-\<buildnumber> as in 6.4-3 which is the 3rd version of the parent pom to use for contrib extension which support XWiki 6.4 version and more.

# Properties

It's possible to customize a bit the behavior of the parent pom using some properties.

## Previous version

By default clirr plugin is executed to check if you broke any API. It automatically find out the previous version but sometime it's not exacting the one you want to compare with.

You can control the version to use as previous version with the property "xwiki.clirr.previous.version" as in:

```xml
  <properties>
    <xwiki.clirr.previous.version>15.0</xwiki.clirr.previous.version>
  </properties>
```

## Nexus plugin

By default the maven artifact are going to be automatically released on http://nexus.xwiki.org. If you want to keep it in too pass (you want to test the deployed artifact before the release or the doing the Maven release is not the same as the one validating the release) you can control the behavior with the properties <xwiki.nexus.skipStaging> and <xwiki.nexus.autoReleaseAfterClose> as in:

```xml
  <properties>
    <!-- Completely skip the Nexus plugin -->
    <xwiki.nexus.skipStaging>true</xwiki.nexus.skipStaging>
    <!-- Disable the automatic release after the clone -->
    <xwiki.nexus.autoReleaseAfterClose>false</xwiki.nexus.autoReleaseAfterClose>
  </properties>
```

## Enable automatic Jira release

If you want to automatically release the (already existing) version on Jira when you release on Maven you can enable it using the Maven property "xwiki.release.jira.skip" as in:

```xml
  <properties>
    <xwiki.release.jira.skip>false</xwiki.release.jira.skip>
  </properties>
```

# Release of a new parent pom

The Maven Release Plugin cannot be used for these pom.xml because one of the goal is to make sure release setup is a clean slate when you use them as parent.

* Go to the right branch
* ./release.sh
