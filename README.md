# Mina SSHD Api Plugin

This plugin wraps [Apache Mina SSHD](https://github.com/apache/mina-sshd) modules as Jenkins plugins. Each module have its own plugins.

# Build

To build the plugin locally:

```
mvn clean verify
```

# Release

The release is automated on Pull Request merge as per [this documentation](https://www.jenkins.io/doc/developer/publishing/releasing-cd/#releasing). To release the plugin, ask the maintainer(s) to merge a PR.

[See the release page](https://github.com/jenkinsci/mina-ssh-api-plugin/releases)

# Test local instance

```
mvn hpi:run
```

# Adding a new Plugin / Module

If in need for a new SSHD module, feel free to open a pull request to add it here. Following this steps:

* Create a new directory `mina-sshd-<name>-api where `<name>` is the name of the SSHD module.
* Create `pom.xml`
    * Add a dependency on `org.apache.sshd:sshd-<name>`.

        ```
        <dependency>
            <groupId>org.apache.sshd</groupId>
            <artifactId>sshd-#MODULE_NAME</artifactId>
            <version>${revision}</version>
        </dependency>
        ```
      
    * Exclude all transitive dependencies
* Create `src/main/resource/index.jelly`
* Add the module to the root `pom.xml`
