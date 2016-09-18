# groovy-project-parent
[![Build Status](https://travis-ci.org/rvenutolo/groovy-project-parent.svg?branch=master)](https://travis-ci.org/rvenutolo/groovy-project-parent)
[![License](https://img.shields.io/hexpm/l/plug.svg)](https://www.apache.org/licenses/LICENSE-2.0)
[![GitHub release](https://img.shields.io/github/release/rvenutolo/groovy-project-parent.svg)](https://github.com/rvenutolo/groovy-project-parent/releases)

A project containing a few POMs intended as parent POMs for my Groovy projects, plus a resources bundle.

## [groovy-project-parent](https://github.com/rvenutolo/groovy-project-parent/blob/master/pom.xml) 
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.venutolo/groovy-project-parent/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.venutolo/groovy-project-parent)
[![Dependency Status](https://www.versioneye.com/user/projects/57c33b3712b526000ed5f3be/badge.svg)](https://www.versioneye.com/user/projects/57c33b3712b526000ed5f3be)

* Top-level parent POM.
* Provides a number of properties that define plugin versions, Groovy and Spock versions, and some other configuration values.
* Provides dependency and plugin versions in `dependencyManagement` and `pluginManagement` elements. All versions can be overridden in child POMs by overwriting a property value.
* Provides a snapshot repository in `distributionManagement`.
* Has one configured build plugin, [`sortpom-maven-plugin`](https://github.com/Ekryd/sortpom), to sort this POM and all inheriting POMs.

```xml
<parent>
    <groupId>org.venutolo</groupId>
    <artifactId>groovy-project-parent</artifactId>
    <version>1.1.0</version>
</parent>
```

## [groovy-project-parent-with-config](https://github.com/rvenutolo/groovy-project-parent/blob/master/groovy-project-parent-with-config/pom.xml) 
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.venutolo/groovy-project-parent-with-config/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.venutolo/groovy-project-parent-with-config)
[![Dependency Status](https://www.versioneye.com/user/projects/57c33bcb86473900106adabe/badge.svg)](https://www.versioneye.com/user/projects/57c33bcb86473900106adabe)

* Child of `groovy-project-parent`.
* Provides default configurations for the plugins defined the parent POM's `pluginManagement` section.
* Does _not_ define any further build plugins.

```xml
<parent>
    <groupId>org.venutolo</groupId>
    <artifactId>groovy-project-parent-with-config</artifactId>
    <version>1.1.0</version>
</parent>
```

## [groovy-project-parent-with-build](https://github.com/rvenutolo/groovy-project-parent/blob/master/groovy-project-parent-with-config/groovy-project-parent-with-build/pom.xml)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.venutolo/groovy-project-parent-with-build/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.venutolo/groovy-project-parent-with-build)
[![Dependency Status](https://www.versioneye.com/user/projects/57c33bd7864739000ec94b20/badge.svg)](https://www.versioneye.com/user/projects/57c33bd7864739000ec94b20)


* Child of `groovy-project-parent-with-config`.
* Provides a default build configuration with plugin configurations inherited from `groovy-project-parent-with-config`.
* Provides a default site build configuration.
* Provides a default `release` profile that adds GPG artifact signing and deploying to OSSRH to the build.

```xml
<parent>
    <groupId>org.venutolo</groupId>
    <artifactId>groovy-project-parent-with-build</artifactId>
    <version>1.1.0</version>
</parent>
```

## [groovy-project-resources](https://github.com/rvenutolo/groovy-project-parent/blob/master/groovy-project-resources/src/main/resources)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/org.venutolo/groovy-project-resources/badge.svg)](https://maven-badges.herokuapp.com/maven-central/org.venutolo/groovy-project-resources)
[![Dependency Status](https://www.versioneye.com/user/projects/57c33b6a8647390016589744/badge.svg)](https://www.versioneye.com/user/projects/57c33b6a8647390016589744)

* Child of `groovy-project-parent`.
* Provides a resource bundle to be used in other projects via the [`maven-remote-resources-plugin`](https://maven.apache.org/plugins/maven-remote-resources-plugin/) plugin. This includes:
 * [Assembly Descriptors](https://maven.apache.org/plugins/maven-assembly-plugin/assembly.html) for creating Groovydoc/Javadoc jars.
 * [CodeNarc](http://codenarc.sourceforge.net/) configuration files.
 * [License Maven Plugin](http://code.mycila.com/license-maven-plugin/) header template.
 * [Maven Site Plugin](https://maven.apache.org/plugins/maven-site-plugin/) site descriptor.
 
 ```xml
 <plugin>
     <groupId>org.apache.maven.plugins</groupId>
     <artifactId>maven-remote-resources-plugin</artifactId>
     <executions>
         <execution>
             <id>get-project-resources</id>
             <goals>
                 <goal>process</goal>
             </goals>
             <phase>generate-resources</phase>
             <configuration>
                 <resourceBundles>
                     <resourceBundle>org.venutolo:groovy-project-resources:${groovy.project.resources.version}</resourceBundle>
                 </resourceBundles>
             </configuration>
         </execution>
         <execution>
             <id>get-site-resources</id>
             <goals>
                 <goal>process</goal>
             </goals>
             <phase>pre-site</phase>
             <configuration>
                 <resourceBundles>
                     <resourceBundle>org.venutolo:groovy-project-resources:${groovy.project.resources.version}</resourceBundle>
                 </resourceBundles>
             </configuration>
         </execution>
     </executions>
 </plugin>
 ```

---
 
### Make Release

```bash
./mvnw "-Darguments=-Dassembly.skipAssembly -Dmaven.source.skip" -B release:clean release:prepare release:perform
```

### Update Maven Wrapper

Use Maven Wrapper plugin
```bash
mvn -N io.takari:maven:wrapper -Dmaven=3.3.9
```

Download latest scripts
```bash
wget https://raw.githubusercontent.com/takari/maven-wrapper/master/mvnw
wget https://raw.githubusercontent.com/takari/maven-wrapper/master/mvnw.cmd
```
