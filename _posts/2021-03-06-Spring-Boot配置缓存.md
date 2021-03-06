---
title: Spring Boot配置缓存
date: 2021-03-06
categories: Spring
tags: cache
---

- pom.xml

  ```xml
  <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-cache</artifactId>
  </dependency>
  <dependency>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-data-redis</artifactId>
  </dependency>
  ```

- application.properties

  ```properties
  spring.cache.type = redis
  spring.cache.cache-names = coffee
  spring.cache.redis.time-to-live = 5000
  spring.cache.redis.cache-null-values = false
  
  spring.redis.host = localhost
  ```

  

