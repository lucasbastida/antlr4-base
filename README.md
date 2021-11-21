# ANTLR4 Base Repository

Reference or starting point for java projects that utilize antlr4, maven and vscode. The following explains the different settings of the project.

# antlr4-maven-plugin configurations

## Adding antlr4-maven-plugin
```xml
<dependencies>
    ...
    <dependency>
      <groupId>org.antlr</groupId>
      <artifactId>antlr4-maven-plugin</artifactId>
      <version>4.9.3</version>
      <type>maven-plugin</type>
    </dependency>
</dependencies>
```

## Adding antlr4-maven-plugin goal
This executes when compiling and will generate your grammars .java files in the `target/generated-sources/antlr4` folder.

note: this does not go inside the `<pluginManagement>` tag
```xml
    <plugins>
      <plugin>
        <groupId>org.antlr</groupId>
        <artifactId>antlr4-maven-plugin</artifactId>
        <version>4.9.3</version>
        <executions>
          <execution>
            <id>antlr</id>
            <goals>
              <goal>antlr4</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
```

## Generating antlr4 visitors or listeners 
Creates BaseListener.java, BaseVisitor.java, Listener.java, Visitor.java files in `target/generated-sources/antlr4` folder
```xml
<properties>
    ...
    <antlr4.visitor>true</antlr4.visitor>
    <antlr4.listener>true</antlr4.listener>
</properties>
```

## Excluding .antlr folder from compiler
Files are generated if you are using vscode extension: ANTLR4 grammar syntax support by Mike Lischke.
```xml
<pluginManagement>
    <plugins>
        ...
        <plugin>
          <artifactId>maven-compiler-plugin</artifactId>
          <version>3.8.0</version>
          <configuration>
            <excludes>
              <exclude>antlr4/com/example/.antlr/**</exclude>
            </excludes>
          </configuration>
        </plugin>
    </plugins>
</pluginManagement>
```

## Solution to common problems

If you end up renaming a grammar filename, for example, example.g4 -> compiler.g4. You have to do one of the following:
- Update your build configuration
- Clean java language server workspace

# References
https://www.antlr.org/api/maven-plugin/latest/