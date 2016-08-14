# groovy-project-parent
[![Build Status](https://travis-ci.org/rvenutolo/groovy-project-parent.svg?branch=master)](https://travis-ci.org/rvenutolo/groovy-project-parent)
[![License](https://img.shields.io/hexpm/l/plug.svg)](https://www.apache.org/licenses/LICENSE-2.0)

A project contaning a few POMs intended as parent POMs for my Groovy projects, plus a resources bundle.

## [groovy-project-parent](pom.xml)

* Top-level parent POM.
* Provides a number of properties that define plugin versions, Groovy and Spock versions, and some other configuration values.
* Provides dependency and plugin versions in `dependencyManagement` and `pluginManagement` elements. All versions can be overriden in child POMs by overwriting a property value.
* Has one configured build plugin, [`sortpom-maven-plugin`](https://github.com/Ekryd/sortpom), to sort this POM and all inherting POMs.

## [groovy-project-parent-with-config](groovy-project-parent-with-config/pom.xml)

* Child of `groovy-project-parent`.
* Provides default configurations for the plugins defined the parent POM's `pluginManagement` section.
* Does _not_ define any further build plugins.

## [groovy-project-parent-with-build](groovy-project-parent-with-config/groovy-project-parent-with-build/pom.xml)

* Child of `groovy-project-parent-with-config`.
* Provides a default build configuration with plugin configurations inherited from `groovy-project-parent-with-config`.
* Provides a default site build configuration.

## [groovy-project-resources](groovy-project-resources/src/main/resources)

* Child of `groovy-project-parent`.
* Provides a resource bundle to be used in other projects via the [`maven-remote-resources-plugin`](https://maven.apache.org/plugins/maven-remote-resources-plugin/) plugin. This includes:
 * [Assembly Descriptiors](https://maven.apache.org/plugins/maven-assembly-plugin/assembly.html) for creating Grooyvdoc/Javadoc jars.
 * [CodeNarc](http://codenarc.sourceforge.net/) configuration files.
 * [License Maven Plugin](http://code.mycila.com/license-maven-plugin/) header template.
 * [Maven Site Plugin](https://maven.apache.org/plugins/maven-site-plugin/) site descriptor.
