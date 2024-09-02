# 自用MosDNS配置

- 支持ECS
- 支持GEOIP
- 支持GEOSITE
- 支持自定义灰名单及白名单
- 支持广告过滤
- 支持数据导入Grafana
- 本层级DNS处理无泄漏

# DNS处理流程：

![image](https://github.com/user-attachments/assets/8b56d92c-c5ec-48dc-8b41-650324f46fad)


根据 [Jasper-1024/mosdns_docker](https://github.com/Jasper-1024/mosdns_docker/tree/master/mosdns_v5)  进行二次修改，在此基础上增加GFW域名远程解析规则，修改并发请求DNS连接数

教程及DNS处理队列详解：[自用MosDNS规则分享](https://www.dolingou.com/article/mosdns-config-with-no-leak)
