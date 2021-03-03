---
title: Spring JPA
date: 2021-03-03
description: 对JPA的理解及应用
categories: Spring
tags: [JPA]
---
<!--!more-->

## 对象与关系的范式不匹配

|          |      Object      |    RDBMS    |
| :------: | :--------------: | :---------: |
|   粒度   |        类        |     表      |
|   继承   |        有        |    没有     |
|  唯一性  | a==b/a.equals(b) |    主键     |
|   关联   |       引用       |    外键     |
| 数据访问 |     逐级访问     | SQL数量减少 |

## Hibernate

> 解放生产力 

## 常用JPA注解

**实体**

- @Entity、@MappedSuperclass
- @Table(name)

**主键**

- @Id
  - @GeneratedValue(strated,generator)
  - @SequenceGenerator(name,sequenceName)

**映射**

- @Column(name,nullable,length,insertable,updatable)
- @JoinTable(name)、@JoinColumn(name)

**关系**

- @OneToOne、@OneToMany、@ManyToOne、@MangToMnay
- @OrderBy

## 源码

https://github.com/digitalsonic/geektime-spring-family