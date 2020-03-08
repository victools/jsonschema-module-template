# Java JSON Schema Generator – Module Template
[![Build Status](https://github.com/victools/jsonschema-module-template/workflows/Java%20CI%20(Maven)/badge.svg)](https://github.com/victools/jsonschema-module-template/actions?query=workflow%3A%22Java+CI+%28Maven%29%22)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.github.victools/jsonschema-module-template/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.github.victools/jsonschema-module-template)

Module for the `jsonschema-generator` – Template

## Features
1. Provide base repository for creating `jsonschema-generator` module libraries.
2. Describe fake template module.

## Usage
### Dependency (Maven)
```xml
<dependency>
    <groupId>com.github.victools</groupId>
    <artifactId>jsonschema-module-template</artifactId>
    <version>n/a</version>
</dependency>
```

### Code
#### Passing into SchemaGeneratorConfigBuilder.with(Module)
```java
import com.github.victools.jsonschema.generator.SchemaGeneratorConfigBuilder;
import com.github.victools.jsonschema.module.template.TemplateModule;
```
```java
TemplateModule module = new TemplateModule();
SchemaGeneratorConfigBuilder configBuilder = new SchemaGeneratorConfigBuilder(objectMapper)
    .with(module);
```

#### Complete Example
```java
import com.fasterxml.jackson.databind.JsonNode;
import com.fasterxml.jackson.databind.ObjectMapper;
import com.github.victools.jsonschema.generator.OptionPreset;
import com.github.victools.jsonschema.generator.SchemaGenerator;
import com.github.victools.jsonschema.generator.SchemaGeneratorConfig;
import com.github.victools.jsonschema.generator.SchemaGeneratorConfigBuilder;
import com.github.victools.jsonschema.module.template.TemplateModule;
```
```java
ObjectMapper objectMapper = new ObjectMapper();
TemplateModule module = new TemplateModule();
SchemaGeneratorConfigBuilder configBuilder = new SchemaGeneratorConfigBuilder(objectMapper, OptionPreset.PLAIN_JSON)
    .with(module);
SchemaGeneratorConfig config = configBuilder.build();
SchemaGenerator generator = new SchemaGenerator(config);
JsonNode jsonSchema = generator.generateSchema(YourClass.class);

System.out.println(jsonSchema.toString());
```
