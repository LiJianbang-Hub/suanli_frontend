算力工坊    

项目描述：基于 Spring Cloud 微服务架构 + MQ + Docker 技术栈构建，提供高效的自动化代码评测服务。平台能够根据管理员配置的题目用例自动执行并评估用户提交的代码。核心功能之一是自主开发的代码沙箱，它可以作为独立服务，供其他开发者调用和集成，提升了平台的灵活性和可扩展性。

工作：
（1）自主设计了判题机模块架构，定义了代码沙箱的抽象接口，并实现了多个具体的沙箱类。通过静态工厂模式和 Spring 配置化管理，实现了对不同类型代码沙箱的灵活切换和调用。

（2）利用 Java Runtime 的 exec 方法实现了 Java 程序的编译和执行，结合 Process 类的输入流获取执行结果，从而搭建了原生的 Java 代码沙箱。    

（3）针对不同的程序异常，编写了 Java 脚本代码来进行沙箱自测，并通过黑白名单和字典树等方式实现了对敏感操作的有效限制，确保了执行过程的安全性。

（4）为确保宿主机的稳定性，使用 Docker 进行用户代码的隔离。通过 Docker Java 库创建容器来运行用户代码，并利用 tty 和 Docker 进行参数交互，从而增强了沙箱的安全性和隔离性。

（5）为提升系统稳定性和模块化，使用 Spring Cloud Alibaba 对项目进行了重构，划分为用户服务、题目服务、判题服务和公共模块。同时，通过 Redis 实现了分布式 Session 存储，确保了用户登录信息的高效管理。

（6）为避免判题操作造成系统阻塞，采用了异步处理方式。在题目服务中，将用户提交的 ID 发送到 RabbitMQ 消息队列，通过 Direct 交换机将消息转发到判题队列，由判题服务异步消费，实时更新提交状态。

简单的demo演示
![image](https://github.com/user-attachments/assets/066cce9c-6097-4d37-a2df-e29dd47995c9)
![image](https://github.com/user-attachments/assets/827f4483-d263-4e86-b5a7-ce4d741fc541)
![image](https://github.com/user-attachments/assets/da54b950-03d9-48f8-bfc7-e18e11a54ad2)
![image](https://github.com/user-attachments/assets/adb078ea-5633-497a-875e-6a5bd36460aa)
![image](https://github.com/user-attachments/assets/0fab82e1-27e4-450e-93c2-3cc250b34503)





