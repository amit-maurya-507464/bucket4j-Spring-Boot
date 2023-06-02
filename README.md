# Spring Boot Rate Limiting - Bucket4j
Spring boot project to implement IP Address based rate limiting on rest APIs by using Bucket4j.

## Runing and Testing
**IDE:** 
Open project in any IDE and run as a spring boot Project. <br>
**Command line:** 
Open terminal and loacte to pom.xml file directory and type command - 
`mvn dpring-boot:run`

Use the following url to test the Application:
http://localhost:8080/swagger-ui/index.html

## Rate Limiting
Rate limiting is a technique to limit network traffic to prevent users from exhausting system resources.
Rate limiting makes it harder for malicious actors to overburden the system and cause attacks like Denial of Service (DoS).
Rate limiting typically involves tracking the IP addresses where requests originate and identifying the time lapsed between requests.
IP addresses are the application's main way to identify who has made each request.
When request quota is consumed, it will throw error with 429 code which is Too many requests.

This Project uses bucket4j for implementing rate limiting.

```
<dependency>
            <groupId>com.github.vladimir-bukhtoyarov</groupId>
            <artifactId>bucket4j-core</artifactId>
            <version>7.4.0</version>
</dependency>
```

![rate-limit.png](assets%2Fimages%2Frate-limit.png)

## Documentation

This project uses springdoc-openapi for documentation.
springdoc-openapi java library helps to automate the generation of API documentation using spring boot projects.

![swagger.png](assets%2Fimages%2Fswagger.png)

**This library supports:**
1. OpenAPI 3
2. Spring-boot (v1, v2 and v3)
3. JSR-303, specifically for @NotNull, @Min, @Max, and @Size.
4. Swagger-ui
5. OAuth 2
6. GraalVM native images

## Rest APIs

It has two APIs to demonstrate rate limiting based on IP Address.
When request quota is consumed, it will throw error with 429 code which is Too many requests.

```
{
"timestamp": "2023-06-02T09:33:08.079+00:00",
"status": 429,
"error": "Too Many Requests",
"message": "",
"path": "/hi"
}
```

## Configuration

We can do configuration of rate limiting from the application.properties file.

```
rate.limit = 3
time.duration.in.minutes = 1
```
1. Rate limit decides how much API requests it will accept for a particular IP Address.
2. Time duration decides the timeframe in which the limit will be reset.


