## 支持的客户端

官方第三方客户端列表：

[https://v2.hysteria.network/zh/docs/getting-started/3rd-party-apps/](https://v2.hysteria.network/zh/docs/getting-started/3rd-party-apps/)

官方客户端安装文档：

[https://v2.hysteria.network/docs/getting-started/Installation/](https://v2.hysteria.network/docs/getting-started/Installation/)

官方客户端配置文档：

[https://v2.hysteria.network/docs/getting-started/Client/](https://v2.hysteria.network/docs/getting-started/Client/)

官方 Releases 下载地址：

[https://github.com/apernet/hysteria/releases](https://github.com/apernet/hysteria/releases)

### v2rayN 使用说明

v2rayN 可通过扫描二维码或导入自定义配置来使用 hysteria2。

#### 方式一：扫描二维码

* V2rayN-windows 可以直接扫描屏幕上的二维码。

#### 方式二：添加自定义配置

* v2rayN 可在自定义配置里添加 hysteria2 原生客户端配置文件，获得更原生的使用体验。
* 如果使用自定义文件启动 hysteria2，自定义 socks 端口请填写 `20808`。
* 添加路径：`v2rayN -> 服务器 -> 添加自定义配置`

![img](../imgs/v2rayN-new.png)

#### 如果提示找不到 hysteria2 core

部分 v2rayN 的打包版本可能不包含 hysteria2 core。如果使用自定义配置启动 hysteria2 时提示找不到 core、启动失败、无对应内核，通常就是因为当前 v2rayN 安装包没有附带 hysteria2 core。此时请按下面步骤手动安装。

##### 第一步：打开 hysteria 官方下载页面

请前往 hysteria 官方 Releases 页面下载最新版本的 core：

[https://github.com/apernet/hysteria/releases](https://github.com/apernet/hysteria/releases)

如果你需要参考官方安装说明，也可以查看：

[https://v2.hysteria.network/docs/getting-started/Installation/](https://v2.hysteria.network/docs/getting-started/Installation/)

##### 第二步：选择与你系统对应的文件

请根据你当前使用的 Windows 系统架构选择对应文件，一般常见情况如下：

* 绝大多数电脑请选择 `windows-amd64`
* 如果你使用的是 ARM 设备，请选择 `windows-arm64`
* 如果你不确定自己的系统架构，通常直接下载 `windows-amd64` 即可

下载后你会得到对应的压缩包或程序文件。

##### 第三步：解压并整理文件

* 如果下载的是压缩包，请先解压。
* 解压后找到 hysteria2 对应的可执行文件。
* 部分文件名可能会带有版本号，这是正常的。

##### 第四步：放到 v2rayN 指定目录

将 hysteria2 的可执行文件放到 v2rayN 程序主目录下的 `bin/hysteria2` 文件夹内。

目录结构示例：

```text
v2rayN/
├─ v2rayN.exe
└─ bin/
   └─ hysteria2/
      └─ hysteria-windows-amd64.exe
```

说明：

* `v2rayN.exe` 所在的位置就是 v2rayN 程序主目录。
* 如果 `bin/hysteria2` 目录不存在，可以手动创建。
* 请确认文件确实放在 `bin/hysteria2` 目录内，不要放错到别的目录。

##### 第五步：重新启动 v2rayN

文件放置完成后：

* 关闭当前正在运行的 v2rayN
* 重新启动 v2rayN
* 再次导入或启动 hysteria2 自定义配置

通常此时就可以正常识别 core。

##### 第六步：如果仍然无法识别

如果仍然提示找不到 core，请继续检查以下内容：

* 你下载的是否为 Windows 对应版本
* 你下载的是否为正确的系统架构版本
* 文件是否已经正确解压
* 可执行文件是否放到了 `v2rayN` 主目录下的 `bin/hysteria2` 中
* 放好文件后是否已经重新启动 v2rayN
* 是否被安全软件拦截、隔离或删除

### 其他使用提示

* 需要发挥 hysteria2 最佳性能时，请在客户端如实填写当前网络下的下行、上行带宽，并填写客户端 QUIC 参数。如果该客户端不支持填写，请使用脚本生成的配置文件或原生客户端。
* v2rayN For Android 需要填写端口跳跃时间才能启动，不然会出错。默认是 `30s`，推荐填写 `120s`。
* 如果没有使用 obfs，直接留空即可。
* clash.meta 目前较好的方案是生成一个配置文件，交由用户自行导入。或者你也可以使用订阅转换，将 URL 转成 clash.meta 可用的订阅。
* nekobox / v2rayN For Android 请在路由设置里打开屏蔽 QUIC 功能，否则无法访问使用了 HTTP/3 的网站。此问题是由于服务器屏蔽了 UDP/443 流量，hysteria 对 UDP 无增强的拥塞控制，可能导致部分网站访问异常。
