# springboot-elk-filebeat-example
Export spring boot logging in json format to ELK stack. One big disadvanrage of traditional plain text log format is that it is hard to handle multiline string, stacktrace, formatted MDCs etc, on approach to solve that is to wrap the log message into json object. To achieve that, add logstash logback encoder to logback config file like this

```xml
<encoder class="net.logstash.logback.encoder.LogstashEncoder"/>
```

and add following dependency

```xml
<dependency>
    <groupId>net.logstash.logback</groupId>
    <artifactId>logstash-logback-encoder</artifactId>
    <version>5.2</version>
    <scope>runtime</scope>
</dependency>
```

Filebeat acts like agent to collect log message and push them to logstash. It is lightweight, supports back pressure with recovery mechanism.