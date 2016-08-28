# groovy-project-parent
[![Build Status](https://travis-ci.org/rvenutolo/groovy-project-parent.svg?branch=master)](https://travis-ci.org/rvenutolo/groovy-project-parent)
[![License](https://img.shields.io/hexpm/l/plug.svg)](https://www.apache.org/licenses/LICENSE-2.0)

A project containing a few POMs intended as parent POMs for my Groovy projects, plus a resources bundle.

## [groovy-project-parent](https://github.com/rvenutolo/groovy-project-parent/blob/master/pom.xml) [![Dependency Status](https://www.versioneye.com/user/projects/57c33b3712b526000ed5f3be/badge.svg?style=flat-square)](https://www.versioneye.com/user/projects/57c33b3712b526000ed5f3be)

* Top-level parent POM.
* Provides a number of properties that define plugin versions, Groovy and Spock versions, and some other configuration values.
* Provides dependency and plugin versions in `dependencyManagement` and `pluginManagement` elements. All versions can be overridden in child POMs by overwriting a property value.
* Provides a snapshot repository in `distributionManagement`.
* Has one configured build plugin, [`sortpom-maven-plugin`](https://github.com/Ekryd/sortpom), to sort this POM and all inheriting POMs.
* Provides a `release` profile that adds a release repository to `distributionManagement` and adds a build plugin, [`maven-gpg-plugin`](https://maven.apache.org/plugins/maven-gpg-plugin/), to sign artifacts.

## [groovy-project-parent-with-config](https://github.com/rvenutolo/groovy-project-parent/blob/master/groovy-project-parent-with-config/pom.xml) [![Dependency Status](https://www.versioneye.com/user/projects/57c33bcb86473900106adabe/badge.svg?style=flat-square)](https://www.versioneye.com/user/projects/57c33bcb86473900106adabe)

* Child of `groovy-project-parent`.
* Provides default configurations for the plugins defined the parent POM's `pluginManagement` section.
* Does _not_ define any further build plugins.

## [groovy-project-parent-with-build](https://github.com/rvenutolo/groovy-project-parent/blob/master/groovy-project-parent-with-config/groovy-project-parent-with-build/pom.xml) [![Dependency Status](https://www.versioneye.com/user/projects/57c33bd7864739000ec94b20/badge.svg?style=flat-square)](https://www.versioneye.com/user/projects/57c33bd7864739000ec94b20)

* Child of `groovy-project-parent-with-config`.
* Provides a default build configuration with plugin configurations inherited from `groovy-project-parent-with-config`.
* Provides a default site build configuration.

## [groovy-project-resources](https://github.com/rvenutolo/groovy-project-parent/blob/master/groovy-project-resources/src/main/resources) [![Dependency Status](https://www.versioneye.com/user/projects/57c33b6a8647390016589744/badge.svg?style=flat-square)](https://www.versioneye.com/user/projects/57c33b6a8647390016589744)

* Child of `groovy-project-parent`.
* Provides a resource bundle to be used in other projects via the [`maven-remote-resources-plugin`](https://maven.apache.org/plugins/maven-remote-resources-plugin/) plugin. This includes:
 * [Assembly Descriptors](https://maven.apache.org/plugins/maven-assembly-plugin/assembly.html) for creating Groovydoc/Javadoc jars.
 * [CodeNarc](http://codenarc.sourceforge.net/) configuration files.
 * [License Maven Plugin](http://code.mycila.com/license-maven-plugin/) header template.
 * [Maven Site Plugin](https://maven.apache.org/plugins/maven-site-plugin/) site descriptor.
