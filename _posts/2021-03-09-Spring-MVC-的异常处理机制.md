---
title: Spring MVC 的异常处理机制
date: 2021-03-09
categories: Spring
tags: MVC
---

## Spring MVC的异常解析

**核心接口**

- HandlerExceptionResolver

**实现类**

- SimpleMappingExceptionResolver
- DefaultHandlerExceptionResolver
- ResponseStatusExceptionResolver
- ExceptionHandlerExceptionResolver

**异常处理方法**

- @ExceptionHandler

**添加位置**

- @Controller / @RestController
- @ControllerAdvice / @RestControllerAdvice