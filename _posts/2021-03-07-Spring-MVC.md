---
title: Spring MVC
date: 2021-03-07
categories: Spring 
tags: MVC
---

初识MVC

<!--more-->

## Spring MVC 常用注解

- @Controller
  - RestController
- @RequestMapping
  - @GetMapping / @PostMapping
  - @PutMapping / @DeleteMapping
  - @RequestBody / @ResponseBody / @ResponseStatus

## Spring MVC 请求处理机制

**绑定一些Attribute**

- WebApplicationContext / LocaleResolver / ThemeResolver

**处理Multipart**

- 如果是，则将请求转为MultipartHttpServeletRequest

**Handler处理**

- 如果找到对应的Handler，执行Controller及前后置处理器逻辑

**处理返回的Model，呈现视图**

## 如何定义处理方法

### 定义映射关系

@Controller

@RequestMapping

- Path / method 指定映射路径与方法
- params / headers 限定映射范围
- consumes / produces 限定请求与响应格式

一些快捷方式

- @RestController
- @GetMapping / @PutMapping / @PostMapping / @DeleteMapping / @PatchMapping 

### 定义处理方法

- @RequestBody / @ResponseBody / @ResponseStatus

- @PathVariable / @RequestParam / @RequestHeader

- HttpEntity / ResponseEntity 

- 详细参数

  https://docs.spring.io/spring/docs/5.1.5.RELEASE/spring-framework-reference/web.html#mvc-ann-arguments

- 详细返回

  https://docs.spring.io/spring/docs/5.1.5.RELEASE/spring-framework-reference/web.html#mvc-ann-return-tpes

### 定义类型转换

自己实现WebMvcConfigurer

- Spring Boot 在WebMvcAutoConfiguration中实现了一个
- 添加自定义的Converter
- 添加自定义的Formatter

### 定义校验

- 通过Validator对绑定结果进行校验
  - Hibernate Validator
- @Valid注解
- BingdingResult

### Multipart上传

- 配置MultipartResolver
  - Spring Boot 自动配置 MultipartAutoConfiguration
- 支持类型multipart/from-data
- MultipartFile类型

## 视图处理

### 视图解析的实现基础

**ViewResolver与View接口**

- AbstractCachingViewResolver
- UrlBasedViewResolver
- FreeMarkerViewResolver
- ContentNegotiatingViewResolver
- InternalResourceViewResolver

**DispatcherServlet中的视图解析逻辑**

- initStrategies()
  - initViewResolvers()初始化了对应ViewResolver
- doDispatch()
  - processDispatchResult()
    - 没有返回视图的话，尝试RequestToViewNameTranslator
    - resolveViewName()解析View对象

**使用@ResponseBody的情况**

- 在HanderAdapter.handle()的中完成了Response的输出
  - RequestMappingHandlerAdapter.invokeHandlerMethod()
    - HandlerMethodReturnValueHandlerComposite.handlerReturnValue()
      - RequestResponseBodyMethodProcessor.handleReturnValue()

### 重定向

**两种不同的重定向前缀**

- redirect
- forward  

