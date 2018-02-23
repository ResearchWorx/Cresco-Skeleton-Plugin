# Cresco-Skeleton-Plugin
The Cresco Skeleton Plugin outlines the most basic pieces required of a plugin for the Cresco framework. Outlined here are the necessary changes to customize this code for your own requirements.

##### Requirements
* Java JDK 1.8+
* Maven 3

##### Where to put my code?
To get your code to run when the plugin is started, simply include a call to it in the `start()` method of the `Plugin.java` file.
```java
public void start() {
    /*
     *  Insert your startup code here
     */
}
```
###### NOTE: Your code can function as a normal Java program as far as using other files and classes, it is simply initialized in this method rather than from `int main(String[] args)` like an ordinary Java program.

If your code requires any cleanup before termination, please add that to the `cleanup()` method of the `Plugin.java` file.
```java
@Override
public void cleanUp() {
    /*
     *  Insert your shutdown / clean up code here
     */
}
```

##### Setting the Plugin's Name:
In order to set the internal name used by Cresco, edit the `pom.xml` file and enter the name in the `<artifactId></artifactId>` tag, located in the following code snippet:
```xml
<plugin>
    <artifactId>maven-assembly-plugin</artifactId>
    <configuration>
        <archive>
            <manifestEntries>
                <artifactId>[PLUGIN NAME]</artifactId>
```
The plugin's version is just the Maven project's version in the `pom.xml` file. Versioning is currently not strictly enforced in Cresco plugins, though that may change in future work.

##### Compiling the JAR file:
All the Maven plugins and code necessary to generate a JAR file are included in the existing `pom.xml`. In order to create the plugin JAR file, simply issue the following command:
```java
mvn clean package
```
This will generate a file in the `target/` directory `<pluginname>-<version>.jar` which can then be read/loaded by the Cresco framework.