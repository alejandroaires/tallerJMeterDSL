# jmeter-java-dsl-sample

En esta carpeta encontraran un proyecto maven con lo basico para comenzar un proyecto de [jmeter-java-dsl](https://abstracta.github.io/jmeter-java-dsl) desde cero.

## Elementos basicos

### Configuración del pom

Es necesario agregar estas dependencias al archivo pom.xml

```
    <dependency>
      <groupId>us.abstracta.jmeter</groupId>
      <artifactId>jmeter-java-dsl</artifactId>
      <version>1.29</version>
      <scope>test</scope>
    </dependency>
```
```
    <dependency>
      <groupId>org.junit.jupiter</groupId>
      <artifactId>junit-jupiter-engine</artifactId>
      <version>5.10.0</version>
      <scope>test</scope>
    </dependency>
```
```
    <dependency>
      <groupId>org.assertj</groupId>
      <artifactId>assertj-core</artifactId>
      <version>3.24.2</version>
      <scope>test</scope>
```