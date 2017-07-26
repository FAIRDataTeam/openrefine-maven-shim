# openrefine-maven-shim
Maven shim for OpenRefine. Installs the OpenRefine jar to your local maven repository so it can be referenced in OpenRefine related maven projects.

## usage
1. Clone the [OpenRefine](https://github.com/OpenRefine/OpenRefine) repository to your local machine
2. Go into the cloned OpenRefine repository and run `./refine linux_dist 2.7`
3. Clone the `openrefine-maven-shim` repository to your local machine
4. Go into the cloned shim repository and run `mvn install:install-file -Dfile=/path/to/openrefine/build/openrefine-2.7.jar -DpomFile=/path/to/shim/pom.xml`
5. Reference the OpenRefine jar in your pom file:
    ```xml
    <dependency>
        <groupId>org.openrefine</groupId>
        <artifactId>openrefine</artifactId>
        <version>2.7</version>
        <scope>provided</scope>
    </dependency>
    ```
   **Note**: the dependency scope is `provided`. When building extensions for OpenRefine, the classes and dependencies for OpenRefine are provided by OpenRefine itself. Setting the dependency scope to `provided` prevents the OpenRefine jar and its transitive dependencies from being packaged into the extension.