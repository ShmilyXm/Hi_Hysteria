## 支持的客户端

### 官方参考链接

* 第三方客户端列表（官方）：  
  [https://v2.hysteria.network/zh/docs/getting-started/3rd-party-apps/](https://v2.hysteria.network/zh/docs/getting-started/3rd-party-apps/)
* 客户端配置文档（官方）：  
  [https://v2.hysteria.network/zh/docs/getting-started/Client/](https://v2.hysteria.network/zh/docs/getting-started/Client/)
* 安装说明（官方）：  
  [https://v2.hysteria.network/zh/docs/getting-started/Installation/](https://v2.hysteria.network/zh/docs/getting-started/Installation/)
* hysteria 官方 Releases 下载地址：  
  [https://github.com/apernet/hysteria/releases](https://github.com/apernet/hysteria/releases)

### 使用前说明

* 如果某个第三方客户端不支持完整填写 hysteria2 参数，那么实际性能、稳定性和功能支持可能会与原生客户端存在差异。
* 如果你更看重完整参数支持、性能调优和原生体验，建议优先使用 hysteria2 原生客户端配置文件。

### 常见客户端说明

* V2rayN-windows 可以直接扫描屏幕上的二维码。
* v2rayN 可在自定义配置里添加 hysteria2 原生客户端配置文件，给予你原汁原味的体验。**如果使用自定义文件启动 hysteria2，那么自定义 socks 端口请填写 20808。**
* 如果 v2rayN 使用自定义配置启动 hysteria2 时提示找不到 core，请自行下载最新版本的 hysteria2 core，并放到 `<v2rayN程序主目录>/bin/hysteria2` 目录中。
* 需要发挥 hysteria2 最佳性能时，请在客户端如实填写当前网络环境下的下行/上行带宽，并根据需要填写客户端 QUIC 参数。如果当前客户端不支持填写，建议优先使用原生配置文件或支持更完整参数的客户端。
* v2rayN For Android 需要填写端口跳跃时间才能启动，不然可能会出错。默认是 30s，推荐填写 120s。
* 如果没有使用 obfs，相关字段直接留空即可。
* clash.meta 目前比较推荐的方案是生成一个配置文件后由用户手动导入。或者也可以自行寻找订阅转换服务，将 URL 转成 clash.meta 可用的订阅格式。
* nekobox / v2rayN For Android 请在路由里面打开屏蔽 QUIC 功能，否则无法访问使用了 HTTP/3 的网站。此问题是因为服务器屏蔽了 UDP/443 流量，而 hysteria 对普通 UDP 流量没有增强拥塞控制，可能导致访问异常。

### v2rayN 添加自定义配置

v2rayN -> 服务器 -> 添加自定义配置

![img](../imgs/v2rayN-new.png)

### v2rayN 使用自定义 hysteria2 配置时提示找不到 core 的解决方法

部分 v2rayN 的打包版本可能不包含 hysteria2 core。如果你在 v2rayN 中使用“自定义配置”启动 hysteria2 时，出现以下情况：

* 提示找不到 core
* 提示缺少 hysteria2 内核
* 启动失败
* 无法运行自定义 hysteria2 配置

通常说明当前 v2rayN 安装目录中没有可用的 hysteria2 程序文件，此时需要手动下载并放置 core。

#### 处理步骤

1. 打开 hysteria 官方 Releases 页面：  
   [https://github.com/apernet/hysteria/releases](https://github.com/apernet/hysteria/releases)

2. 在 Releases 页面中下载最新版本的客户端程序。  
   请根据你的系统架构选择对应文件：
   * Windows 64 位系统通常选择 `windows-amd64`
   * Windows ARM 设备通常选择 `windows-arm64`

3. 下载完成后，将压缩包解压，得到对应的 hysteria2 程序文件。

4. 打开 v2rayN 程序主目录，进入以下目录：  
   `<v2rayN程序主目录>/bin/hysteria2`

5. 如果 `bin/hysteria2` 目录不存在，可以手动创建。

6. 将解压后的 hysteria2 程序文件放入 `bin/hysteria2` 目录中。

7. 放置完成后，重新启动 v2rayN。

8. 再次导入或启动 hysteria2 自定义配置。

#### 检查要点

如果仍然提示找不到 core，请检查以下内容：

* 是否下载了正确系统和架构的版本
* 是否已经先解压，而不是把压缩包直接放进去
* hysteria2 core 是否放在 `<v2rayN程序主目录>/bin/hysteria2`
* v2rayN 是否已经完全退出并重新启动
* 当前使用的 v2rayN 版本是否支持 hysteria2 / 自定义 core 调用
