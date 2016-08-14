# groovy-project-parent
[![Build Status](https://travis-ci.org/rvenutolo/groovy-project-parent.svg?branch=master)](https://travis-ci.org/rvenutolo/groovy-project-parent)
[![License](https://img.shields.io/hexpm/l/plug.svg)](https://www.apache.org/licenses/LICENSE-2.0)

A project contaning a few POMs intended as parent POMs for my Groovy projects, plus a resources bundle.

## [groovy-project-parent](pom.xml)

* Top-level parent POM.
* Has a number of properties that define plugin versions, Groovy and Spock versions, and some other configuration values.
* Provides dependency and plugin management.
* Has one configured plugin, [`sortpom-maven-plugin`](https://github.com/Ekryd/sortpom), in the build section to sort this and all inherting POMs.

## [groovy-project-parent-with-config](groovy-project-parent-with-config/pom.xml)

## [groovy-project-parent-with-build](groovy-project-parent-with-config/groovy-project-parent-with-build/pom.xml)

## [groovy-project-resources](groovy-project-resources/pom.xml)
