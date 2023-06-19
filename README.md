# Java

This is a Java engine used to launch Java apps on [Microbox](http://microbox.cloud).

## Usage
To use the Java engine, specify `java` as your `engine` in your boxfile.yml.

```yaml
run.config:
  engine: java
```

## Build Process
When [running a build](https://docs.nanboox.io/cli/build/), this engine compiles code by doing the following:

Maven (you can customize with the `compile` option in the [maven settings](#maven-settings):
- `mvn -B -DskipTests=true clean install`

Gradle (you can customize with the `compile` option in the [gradle settings](#gradle-settings)):
- `gradle build`

## Basic Configuration Options
This engine exposes configuration options through the [boxfile.yml](https://docs.microbox.cloud/app-config/boxfile/), a yaml config file used to provision and configure your app's infrastructure when using Microbox.


#### Overview of Basic Boxfile Configuration Options

```yaml
run.config:
  engine.config:
    # Java Settings
    runtime: oracle-jdk8

    # Maven Settings
    maven_version: '3.3'

    # Gradle Settings
    gradle_version: '4.2'

    # Node.js Settings
    nodejs_runtime: nodejs-4.4
```

##### Quick Links
[Java Settings](#java-settings)
[Maven Settings](#maven-settings)
[Gradle Settings](#gradle-settings)
[Node.js Settings](#node-js-settings)

---

### Java Settings
The following setting allows you to define your Java runtime environment.

---

#### runtime
Specifies which Java runtime and version to use. The following runtimes are available:

- openjdk7
- openjdk8
- oracle-jdk8 *(default)*
- sun-jdk6
- sun-jdk7
- sun-jdk8

```yaml
run.config:
  engine.config:
    runtime: openjdk8
```

---

### Maven Settings
The following setting allows you to configure Maven to your specific needs.

---

#### maven_version
Defines which version of Maven to use. Available versions depend on which version of Java you're using.

##### Java 6
- 3.0
- 3.1
- 3.2

##### Java 7
- 3.0
- 3.1
- 3.2
- 3.3

#### Java 8
- 3.0
- 3.1
- 3.2
- 3.3

```yaml
run.config:
  engine.config:
    maven_version: '3.3'
```
#### compile

Define a custom build command. Useful if you need to do something other than the default `mvn -T 4.0C -B -DskipTests=true clean install` like `mvn package`.

```yaml
run.config:
  engine.config:
    maven_version: '3.3'
    compile: 'mvn clean package'
```

---

### Gradle Settings

If you want to use the [Gradle](https://gradle.org) build tool, you can configure which version you want to use.
The following settings are valid:

#### gradle_version

Defines which version of Gradle to use from the [distribution list](https://services.gradle.org/distributions/).

```yaml
run.config:
  engine.config:
    gradle_version: '4.2'
```

#### compile

Define a custom build command. Useful if you need to do something other than the default `gradle build` like `gradle shadowJar`.

```yaml
run.config:
  engine.config:
    gradle_version: '4.2'
    compile: 'gradle shadowJar'
```


---

### Node.js Settings
Many applications utilize Javascript tools in some way. This engine allows you to specify which Node.js runtime you'd like to use.

---

#### nodejs_runtime
Specifies which Node.js runtime and version to use. You can view the available Node.js runtimes in the [Node.js engine documentation](https://github.com/mu-box/microbox-engine-nodejs#runtime).

```yaml
run.config:
  engine.config:
    nodejs_runtime: nodejs-4.4
```

---

## Help & Support
This is a Java engine provided by [Microbox](http://microbox.cloud). If you need help with this engine, you can reach out to us in the [Microbox Discord](https://discord.gg/MCDdHfy). If you are running into an issue with the engine, feel free to [create a new issue on this project](https://github.com/mu-box/microbox-engine-java/issues/new).
