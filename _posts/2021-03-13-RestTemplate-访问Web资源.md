---
title: RestTemplate 访问Web资源
date: 2021-03-13
categories: Spring
tags: RestTemplate
---

## Spring Boot 中的RestTemplate

- Spring Boot 中没有自动配置RestTemplate
- Spring Boot 提供了RestTemplateBuilder
  - RestTemplate.build()

### 构造URL

```java
URI uri = Uri ComponentsBuilder
		.fromUriString("http://example.com/hotels/{hotel}")
		.queryParam("q","{q}")
   		.encode()
		.buildAndExpand("Westin","123")
		.toUri();
//更为简洁
URI uri = UriComponentsBuilder
		.fromUriString("http://example.com/hotels/{hotel}?q={q}"
        .build("Westin","123");
                       
UriComponents uriComponents = MvcUriComponentsBuilder
	.fromMethodCal1(on(BookingController.class).getBooking(21)).buildAndExpand(42);
URI uri = uriComponents.encode().toUri();
```

## Rest

> "REST提供了一组架构约束，当作为一个整体来应用时，强调组件交互的
> 可伸缩性、接口的通用性、组件的独立部署、以及用来减少交互延迟、增
> 强安全性、封装遗留系统的中间组件。”
>
> Roy Thomas Fielding

### Richardson 成熟度模型

[![6wEgsJ.png](https://s3.ax1x.com/2021/03/13/6wEgsJ.png)](https://imgtu.com/i/6wEgsJ)

### 如何实现 Restful Web Service

- 识别资源

- 选择合适的资源粒度

- 设计URL

- 选择合适的 HTTP 方法和返回码

- 设计资源的表述

  #### 识别资源

  - 找到领域名词
    - 能用CRUD操作的名词
  - 将资源组织为集合（即集合资源）
  - 将资源合并为复合资源
  - 计算或处理函数

  #### 资源的粒度

  **站在服务端的角度，要考虑**

  - 网络效率
  - 表述的多少
  - 客户端的易用程度

  **站在客户端的角度，要考虑**

  - 可缓存性
  - 修改频率
  - 可变性
  
  #### 构建更好的URL
  
  - 使用域及子域对资源进行合理的分组或划分
  - 在URI的路径部分使用斜杠分隔符（/)来表示资源之间的层次关系
  - 在URI的路径部分使用逗号（,)和分号（;)来表示非层次元素
  - 使用连字符（-)和下划线（_)来改善长路径中名称的可读性
  - 在URI的查询部分使用“与”符号（&)来分隔参数
  - 在URI中避免出现文件扩展名（例如.php,.aspx和.jsp)
  
  #### 认识HTTP方法
  
  [![6wNofU.png](https://s3.ax1x.com/2021/03/13/6wNofU.png)](https://imgtu.com/i/6wNofU)
  
  #### 认识HTTP状态码
  
  [![6waebR.png](https://s3.ax1x.com/2021/03/13/6waebR.png)](https://imgtu.com/i/6waebR)
  
  