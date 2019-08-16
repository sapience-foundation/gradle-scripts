Sapience Foundation - Gradle Scripts
==============

A simple way to use Gradle with your projects.

Java - Single Project (defining variables at gradle.properties)
----

- /gradle.properties
  ```
  theEmail=your@email.com
  defaultArtifactGroup=com.your.company
  ```

- /build.gradle
  ```
  apply from: 'https://raw.githubusercontent.com/sapience-foundation/gradle-scripts/master/v5/single-project-java8.gradle'
  
  dependencies {
    compile group: 'org.slf4j', name: 'slf4j-api', version: '1.7.7'
    compile group: 'ch.qos.logback', name: 'logback-classic', version: '1.1.2'
    
    testCompile group: 'junit', name: 'junit', version: '4.11'
  }
  
  ```
  
Java - Single Project (defining variables with remote configuration file)
----

- https://securezone.your-company.com/gradle-config/projects-config.gradle
  ```
  ext {
    theEmail = "your@email.com"
    defaultArtifactGroup = "com.your.company"
  }
  ```

- /build.gradle
  ```
  apply from: 'https://securezone.your-company.com/gradle-config/projects-config.gradle'
  apply from: 'https://raw.githubusercontent.com/sapience-foundation/gradle-scripts/master/v5/single-project-java8.gradle'
  
  dependencies {
    compile group: 'org.slf4j', name: 'slf4j-api', version: '1.7.7'
    compile group: 'ch.qos.logback', name: 'logback-classic', version: '1.1.2'
    
    testCompile group: 'junit', name: 'junit', version: '4.11'
  }
  
  ```
  
Java - Multi Project
----

You should define `gradle.properties` or a `remote configuration file` as in example above:

- /build.gradle
  ```
  apply from: 'https://raw.githubusercontent.com/sapience-foundation/gradle-scripts/master/v5/multi-project-java8.gradle'
  
  ```
  
- /sub-project-a/build.gradle
  ```
  dependencies {
    compile group: 'org.slf4j', name: 'slf4j-api', version: '1.7.7'
    compile group: 'ch.qos.logback', name: 'logback-classic', version: '1.1.2'
    
    testCompile group: 'junit', name: 'junit', version: '4.11'
  }
  
  ```
  
- /sub-project-b/build.gradle
  ```
  dependencies {
    compile project(':sub-project-a')
    
    testCompile group: 'junit', name: 'junit', version: '4.11'
  }
  ```


