# groovy-project-parent
[![Build Status](https://travis-ci.org/rvenutolo/groovy-project-parent.svg?branch=master)](https://travis-ci.org/rvenutolo/groovy-project-parent)
[![License](https://img.shields.io/hexpm/l/plug.svg)](https://www.apache.org/licenses/LICENSE-2.0)

A project contaning a few POMs intended as parent POMs for my Groovy projects, plus a resources bundle.

## [groovy-project-parent](pom.xml)

* Top-level parent POM.
* Provides a number of properties that define plugin versions, Groovy and Spock versions, and some other configuration values.
* Provides dependency and plugin versions in `dependencyManagement` and `pluginManagement` elements.
* Has one configured plugin, [`sortpom-maven-plugin`](https://github.com/Ekryd/sortpom), defined in the build element to sort this POM and all inherting POMs.

## [groovy-project-parent-with-config](groovy-project-parent-with-config/pom.xml)

* Child of `groovy-project-parent`.
* Provides a default configuration for the plugins defined the parent POM's `pluginManagement` section.
* Does _not_ define any more plugins for the project build.

## [groovy-project-parent-with-build](groovy-project-parent-with-config/groovy-project-parent-with-build/pom.xml)

## [groovy-project-resources](groovy-project-resources/pom.xml)
