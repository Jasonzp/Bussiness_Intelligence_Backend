# AI 数据可视化平台

> 作者：[zzp](https://github.com/Jasonzp)
> 仅分享于 [我的Github 主页](https://github.com/Jasonzp)

![image](https://github.com/user-attachments/assets/d16f46cc-afff-443e-9234-974e793cc539)  
![image](https://github.com/user-attachments/assets/10bc891f-aad6-41df-b169-73e38e610de6)


[toc]

## 技术选型
### 前端
+ React 18
+ Ant Design Pro 5.x脚手架
+ Umi4 前端框架
+ Ant Design 组件库
+ Echarts 可视化库
+ OpenAPI前端代码生成
### 后端  
+ Java Spring Boot(万用后端模板)
+ MySQL数据库
+ MyBatis-Plus及MyBatisx自动生成
+ Redis + Redisson 限流
+ RabbitMQ 消息队列。
+ 星火大模型 AI SDK(AI能力)
+ JDK 线程池及异步化
+ Easy Excel表格数据处理
+ Swagger + Knife4j 接口文档生成
+ Hutool、Apache Common Utils 等工具库
## 项目亮点
1.后端自定义 Prompt 预设模板并封装用户输入的数据和分析诉求，通过对接 AIGC 接口生成可视化图表 json 配置和分析结论，返回给前端染。  
2.由于 AIGC 的输入 Token 限制，使用 Easy Excel 解析用户上传的 XLSX 表格数据文件并压缩为 CSV，实测提高了 20% 的单次输入数据量、并节约了成本。  
3.为保证系统的安全性，对用户上传的原始数据文件进行了后缀名、大小、内容等多重校验  
4.为防止某用户恶意占用系统资源，基于 Redisson 的 RateLimiter 实现分布式限流，控制单用户访问的频率。    
5.由于 AIGC 的响应时间较长,基于自定义 I0 密集型线程池 + 任务队列实现了 AIGC 的并发执行和异步化，提交任务后即可响应前端，提高用户体验。  
6.由于本地任务队列重启丢失数据,使用 RabbitMO 来接受并持久化任务消息，通过 Direct 交换机转发给解耦的 AI生成模块消费并处理任务，提高了系统的可靠性。
