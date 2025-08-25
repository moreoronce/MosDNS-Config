# 自用MosDNS配置

- 支持ECS
- 支持GEOIP
- 支持GEOSITE
- 支持自定义灰名单及白名单
- 支持广告过滤
- 支持数据导入Grafana
- 本层级DNS处理无泄漏

# 使用方法

配置文件共计**3**个，分别为`config_custom.yaml`, `dns.yaml`, `dat_exec.yaml` 。

各部分作用如下：

- `config_custom.yaml`: 主配置文件，负责DNS序列定义以及DNS序列执行。需要依赖`dns.yaml`和`dat_exec.yaml`运行。
- `dns.yaml`: dns定义配置文件，负责配置公共DNS服务器及远端解析DNS地址及端口。
- `dat_exec.yaml`: 规则配置文件，负责定义各规则tag及规则来源文件。

下载或克隆三个yaml文件，OpenWRT放到`/etc/mosdns`文件夹内。如果是luci-app-mosdns，需要选择使用自定义配置文件。其他系统可以通过`-c` 参数指定配置文件为`config_custom.yaml` 。

默认GeoSite和GeoIP的存放位置为`/var/mosdns/` ,请确保文件夹下含有`geoip_cn.txt`、`geosite_category-ads-all.txt`、`geosite_geolocation-!cn.txt`、`geosite_gfw.txt`、`geosite_cn.txt`以及`geoip_private.txt` ，OpenWRT用户可以通过luci-app-mosdns的GeoData Export功能自动下载解码生成。
同时，在/etc/mosdns/下需要建立rule文件夹，并新建whitelist.txt和greylist.txt文件，用于自定义白名单和污染域名名单。DDNS类域名可放到白名单中。

# DNS处理流程：

![image](https://github.com/user-attachments/assets/8b56d92c-c5ec-48dc-8b41-650324f46fad)


根据 [Jasper-1024/mosdns_docker](https://github.com/Jasper-1024/mosdns_docker/tree/master/mosdns_v5)  进行二次修改，在此基础上增加GFW域名远程解析规则，修改并发请求DNS连接数

教程及DNS处理队列详解：[自用MosDNS规则分享](https://www.dolingou.com/article/mosdns-config-with-no-leak)
