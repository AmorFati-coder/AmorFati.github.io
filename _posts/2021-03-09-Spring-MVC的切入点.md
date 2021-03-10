---
title: Spring MVC的切入点
date: 2021-03-09
categories: Spring
tags: 
---

## Spring MVC 的拦截器

**核心接口**

- HandlerInterceptor
  - boolean preHandle()
  - void postHandle()
  - void afterHandle()

**针对@ReponseBody和ResponseEntity的情况**

- ResponseBodyAdvice

**针对异步请求的接口**

- AsyncHandlerInterceptor
  - void afterConcurrentHandlingStarted()

## 拦截器的配置方式

**常规方法**

- WebMvcConfigurer.addInterceptors()

**Spring Boot 中的配置**

- 创建一个带@Configuration的WebMvcConfiguration配置类
- 不能带@EnableWebMvc