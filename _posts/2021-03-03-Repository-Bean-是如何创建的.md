---
title: Repository Bean 是如何创建的
date: 2021-03-03
catgories: Spring
tags: Bean
---

## Repository的创建

**JpaRepositoriesRegister**

- 激活了@EnableJpaRepositories
- 返回了JpaRepositoryConfigExtension

**RepositoryBeanDefinitionRegistrarSupport.registerBeanDefinitions**

- 注册Repository Bean (类型是JpaRepositoryFactoryBean)

**RepositoryConfigurationExtensionSupport.getRepositoryConfigurations**

- 取得Repository配置

JpaRepositoryFactory.getTargetRepository

- 创建了Repository

## 接口中的方法是如何被解释的

**RepositoryFactorySupport.getRepository添加了Advice**

- DefaultMethodInvokingMethodInterceptor
- QueryExcutorMethodInterceptor

**AbstarctJpaQuery.execute执行具体的查询**

语法解析在Part中



