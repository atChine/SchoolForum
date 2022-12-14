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
- [x] 置顶、加精、删除
- [x] 网站统计



