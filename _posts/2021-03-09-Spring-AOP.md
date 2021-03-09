---
title: Spring AOP
date: 2021-03-09
categories: Spring
tags: AOP
---

## 核心概念
| 概念          | 含义                                              |
| ------------- | ------------------------------------------------- |
| Aspect        | 切面                                              |
| Join Point    | 连接点，Spring AOP总是代表一次方法执行            |
| Advice        | 通知，在连接点执行的动作                          |
| Pointcut      | 切入点，说明如何匹配连接点                        |
| Introduction  | 引入，为现有类型声明额外的方法和属性              |
| Target object | 目标对象                                          |
| AOP proxy     | AOP代理对象，可以是JDK动态代理，也可以是CGLIB代理 |
| Weaving       | 织入，连接切面与目标对象或类型创建代理的过程      |

## 常用注解

- @EnableAspectJpaAutoProxy

  

- @Aspect

  切面是`Pointcut`和`Advice`的集合，一般单独作为一个类。`Pointcut`和`Advice`。共同定义了关于切面的全部内容。`@Aspect` 修饰的类要么是用 `@Component`注解修饰，要么是在 XML中配置过的。

- @Pointcut

  这是应用程序中使用Spring AOP框架采取操作的实际位置。

- @Before

- @Advice

  这是应用程序中使用Spring AOP框架采取操作的实际位置。

- @After / @AfterReturning / @AfterThrowing

- @Around 

- @Order

## 如何打印SQL

### **HikariCP**

- P6Spy, http://github.com/p6spy/p6spy

**Alibaba Druid**

- 内置SQL输出
- http://github.com/alibaba/druid/wiki/Druid中使用log4j2输出