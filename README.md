# simple-java-maven-app

<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.example</groupId>
  <artifactId>demo-app</artifactId>
  <version>1.0.0</version>

  <properties>
    <maven.compiler.source>17</maven.compiler.source>
    <maven.compiler.target>17</maven.compiler.target>
  </properties>

  <build>
    <plugins>
      <!-- Nexus IQ CLI Plugin -->
      <plugin>
        <groupId>org.sonatype.clm</groupId>
        <artifactId>clm-maven-plugin</artifactId>
        <version>2.41.0</version>
      </plugin>

      <!-- CycloneDX for SBOM -->
      <plugin>
        <groupId>org.cyclonedx</groupId>
        <artifactId>cyclonedx-maven-plugin</artifactId>
        <version>2.7.8</version>
        <executions>
          <execution>
            <phase>verify</phase>
            <goals>
              <goal>makeBom</goal>
            </goals>
          </execution>
        </executions>
      </plugin>
    </plugins>
  </build>
</project>
