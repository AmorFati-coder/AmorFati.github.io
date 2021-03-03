---
title: Spring JPA
date: 2021-03-03
description: Spring Data JPA annotation
categories: Spring
tags: JPA
---
<!--!more-->

## table

`@MappedSuperclass` 是类级别注解，该注解没有任何参数，被该注解标注的类不会映射到数据库中单独的表，但该类所拥有的属性都将映射到其子类的数据库表的列中。

`@Entity`注释指名这是一个实体Bean，@Table注释指定了Entity所要映射带数据库表，其中@Table.name()用来指定映射表的表名。
如果缺省@Table注释，系统默认采用类名作为映射表的表名。实体Bean的每个实例代表数据表中的一行数据，行中的一列对应实例中的一个属性。

`@Column`注释定义了将成员属性映射到关系表中的哪一列和该列的结构信息，属性如下：
1）name：映射的列名。如：映射tbl_user表的name列，可以在name属性的上面或getName方法上面加入；
2）unique：是否唯一；
3）nullable：是否允许为空；
4）length：对于字符型列，length属性指定列的最大字符长度；
5）insertable：是否允许插入；
6）updatetable：是否允许更新；
7）columnDefinition：定义建表时创建此列的DDL；
8）secondaryTable：从表名。如果此列不建在主表上（默认是主表），该属性定义该列所在从表的名字。
`@Id`注释指定表的主键，它可以有多种生成方式：

1）TABLE：容器指定用底层的数据表确保唯一；
2）SEQUENCE：使用数据库德SEQUENCE列莱保证唯一（Oracle数据库通过序列来生成唯一ID）；
3）IDENTITY：使用数据库的IDENTITY列莱保证唯一；
4）AUTO：由容器挑选一个合适的方式来保证唯一；
5）NONE：容器不负责主键的生成，由程序来完成。

`@GeneratedValue`注释定义了标识字段生成方式。

`@Temporal`注释用来指定java.util.Date或java.util.Calender属性与数据库类型date、time或timestamp中的那一种类型进行映射。

`@Temporal`(value=TemporalType.TIME)

## 映射规则

映射规则：

1. 实体类**必须**用 @javax.persistence.**Entity** 进行注解；

2. **必须**使用 @javax.persistence.**Id** 来注解一个主键；

3. 实体类必须拥有一个 **public 或者 protected** 的**无参**构造函数，之外实体类还可以拥有其他的构造函数；

4. 实体类必须是一个**顶级类**（top-level class）。一个枚举（enum）或者一个接口（interface）不能被注解为一个实体；

5. 实体**类**不能是 **final 类型**的，也**不能有 final 类型**的方法；

6. 如果实体类的一个实例需要用传值的方式调用（例如，远程调用），则这个实体类必须实现（implements）java.io.Serializable 接口。 

## Repository

- CrudRepository <T ,ID>一些简单的方法
- PagingAndSortingRepository<T, ID> 
- JpaRepository<T, ID>

`@enableJpaRepository`

**定义查询**

- find By/read By/query By/get By
- count By
-  OrderBy [Asc / Desc]
- And / Or / IgnoreCase
- Top / First / Distinct

**分页查询**

- PagingAndSortingRepository<T,ID>
- Pageable / Sort
- Slice<T> / Page<T>

**查询实体**

`NoRepositoryBean`仅在开始扩展具有功能的所有存储库时才需要它

