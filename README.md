Sapience Foundation - Gradle Scripts
==============

A simple way to use Gradle with your projects.

Java - Single Project (defining variables at gradle.properties)
----

- /gradle.properties
  ```
  gradleScriptsPath=https://raw.githubusercontent.com/sapience-foundation/gradle-scripts/master
  organizationEmail=your@email.com
  organizationArtifactGroup=com.your.company
  ```

- /build.gradle
  ```
  apply from: "${gradleScriptsPath}/v5/single-project-java8.gradle"
  
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
    gradleScriptsPath = "https://raw.githubusercontent.com/sapience-foundation/gradle-scripts/master"
    organizationEmail = "your@email.com"
    organizationArtifactGroup = "com.your.company"
  }
  ```

- /build.gradle
  ```
  apply from: 'https://securezone.your-company.com/gradle-config/projects-config.gradle'
  apply from: "${gradleScriptsPath}/v5/single-project-java8.gradle"
  
  dependencies {
    compile group: 'org.slf4j', name: 'slf4j-api', version: '1.7.7'
    compile group: 'ch.qos.logback', name: 'logback-classic', version: '1.1.2'
    
    testCompile group: 'junit', name: 'junit', version: '4.11'
  }
  
  ```
  
Java - Multi Project
----

- /gradle.properties

You should define `gradle.properties` or a `remote configuration file` as in example above.

- /build.gradle
  ```
  apply from: "${gradleScriptsPath}/master/v5/multi-project-java8.gradle"
  
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

