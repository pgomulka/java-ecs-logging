# Log4j2 ECS Layout

## Step 0: build the project
Check out the project and build with `mvn clean install`.
Once this project is available on maven central, this step is no longer needed.

## Step 1: add dependency

Add a dependency to your application
```xml
<dependency>
    <groupId>co.elastic.logging</groupId>
    <artifactId>log4j2-ecs-layout</artifactId>
    <version>${java-ecs-logging.version}</version>
</dependency>
```

## Step 2: use the `EcsLayout`

Instead of the usual `<PatternLayout/>`, use `<EcsLayout serviceName="my-app"/>`

## Example
```xml
<?xml version="1.0" encoding="UTF-8"?>
<Configuration status="DEBUG" packages="co.elastic.logging.log4j2">
    <Appenders>
        <Console name="LogToConsole" target="SYSTEM_OUT">
            <EcsLayout serviceName="my-app"/>
        </Console>
        <File name="LogToFile" fileName="logs/app.log">
            <EcsLayout serviceName="my-app"/>
        </File>
    </Appenders>
    <Loggers>
        <Root level="info">
            <AppenderRef ref="LogToFile"/>
            <AppenderRef ref="LogToConsole"/>
        </Root>
    </Loggers>
</Configuration>
```
