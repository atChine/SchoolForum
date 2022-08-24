# 校园论坛项目

![IDE](https://img.shields.io/badge/IDE-IntelliJ%20IDEA-brightgreen.svg) ![Java](https://img.shields.io/badge/Java-1.8-blue.svg) ![Database](https://img.shields.io/badge/Database-MySQL-lightgrey.svg)

## 项目简介
本项目是一个校内互动交流平台，主要涉及模块有权限模块、帖子模块、性能模块、通知模块、搜索模块。主要实现了用户的注册、登录、发帖、点赞、系统通知、按热度排序、搜索等功能。另外引入了redis数据库来提升网站的整体性能，实现了用户凭证的存取、点赞关注的功能。基于 Kafka 实现了系统通知：当用户获得点赞、评论后得到通知。利用定时任务定期计算帖子的分数，并在页面上展现热帖排行榜。

| 用户类型 | 用户名 | 密码   |权限|
| -------- | ------ | ------ |------ |
| 普通用户 | aaa   | aaa |无权限 |
| 版主     | nowcoder21 | 123456 |置顶、加精权限 |
| 管理员   | nowcoder11  | 123456 |置顶、加精、删帖权限 |

## 技术栈

| 技术            | 链接                                                         | 版本           |
| --------------- | ------------------------------------------------------------ | -------------- |
| Spring Boot     | https://spring.io/projects/spring-boot                       | 2.4.3          |
| Spring          | https://spring.io/projects/spring-framework                  | 5.3.4          |
| Spring MVC      | https://docs.spring.io/spring-framework/docs/current/reference/html/web.html#spring-web | 5.3.4          |
| MyBatis         | http://www.mybatis.org/mybatis-3                             | 3.5.1          |
| Redis           | https://redis.io/                                            | 5.0.3          |
| Kafka           | http://kafka.apache.org/                                     | 2.7.0          |
| Elasticsearch   | https://www.elastic.co/cn/elasticsearch/                     | 7.9.3          |
| Spring Security | https://spring.io/projects/spring-security                   | 5.4.5          |
| Spring Quartz   | https://www.baeldung.com/spring-quartz-schedule              | 2.3.2          |
| wkhtmltopdf     | https://wkhtmltopdf.org                                      | 0.12.6         |
| kaptcha         | https://github.com/penggle/kaptcha                           | 2.3.2          |
| Thymeleaf       | https://www.thymeleaf.org/                                   | 3.0.12.RELEASE |
| MySQL           | https://www.mysql.com/                                       | 5.7.17         |
| JDK             | https://www.oracle.com/java/technologies/javase-downloads.html | 1.8            |


## 功能列表


- [x] 注册
- [x] 邮件发送
- [x] 验证码
- [x] 登录
- [x] 修改密码
- [x] 敏感词过滤
- [x] 发布帖子
- [x] 我的帖子
- [x] 帖子详情
- [x] 评论
- [x] 私信
- [x] 统一异常处理
- [x] 统一日志处理
- [x] 点赞
- [x] 关注
- [x] 系统通知
- [x] 搜索
- [x] 权限控制
- [x] 置顶、加精、删除
- [x] 网站统计
- [x] 定时执行任务计算热门帖子


## 功能简介

- 使用 Redis 的 set 实现点赞，zset 实现关注，并使用 Redis 存储登录ticket和验证码，解决分布式 Session 问题，使用 Redis 的高级数据类型 HyperLogLog 统计 UV (Unique Visitor)，使用 Bitmap 统计 DAU (Daily Active User)。
- 使用Redis Cell模块对用户发帖进行限流，防止恶意灌水。
- 使用 Kafka 处理发送评论、点赞、关注等系统通知、将新发布的帖子异步传输至Elasticsearch服务器，并使用事件进行封装，构建了强大的异步消息系统。
- 使用Elasticsearch做全局搜索，增加关键词高亮显示等功能。
- 热帖排行模块，使用本地缓存 Caffeine作为一级缓存和分布式缓存 Redis作为二级缓存构建多级缓存，避免了缓存雪崩，同时使用使用压测工具测试优化前后性能，将 QPS 提升了4.1倍 (5.5/sec -> 22.5/sec)，提升了网站访问速度。
- 使用 Spring Security 做权限控制，替代拦截器的拦截控制，并使用自己的认证方案替代 Security 认证流程，使权限认证和控制更加方便灵活。


## 系统架构

![image-20210331103427522](https://gitee.com/zhengguohuang/img/raw/master/img/image-20210331103427522.png)

![网站架构图](https://gitee.com/zhengguohuang/img/raw/master/img/%E7%BD%91%E7%AB%99%E6%9E%B6%E6%9E%84%E5%9B%BE.png)

