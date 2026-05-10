#### Realm 模式（P2P 穿透）

Realm 是 Hysteria 2 的 P2P 穿透模式，允许服务器在**无公网 IP、无端口转发**的环境下运行。

##### 工作原理

1. 服务器通过 STUN 发现自己的公网 UDP 地址，将其注册到牵手（rendezvous）服务器
2. 客户端使用相同的 realm 名向牵手服务器请求连接
3. 牵手服务器交换双方的地址信息，双方同时向对方发送 UDP 包进行打洞
4. 打洞成功后，流量直接在服务器和客户端之间传输，**不经过牵手服务器**

##### 适用场景

- 家庭宽带 NAT 后（无公网 IP）
- CGNAT 环境
- 咖啡厅/酒店/热点网络
- 快速测试，无需配置 VPS

##### 注意事项

- 官方公共牵手服务器地址为 `realm.hy2.io`，使用密码 `public`
- Realm 名使用随机 UUID 生成，**请勿泄露**，知道此名称的人可以获得你的服务器 IP 地址
- 目前仅支持使用 hysteria core 直接运行的客户端，不支持分享链接和 ClashMeta 配置
- Realm 模式下不需要配置端口、端口跳跃，无需操作防火墙
- 自签证书无需检测公网 IP，直接使用牵手地址连接
- 支持自建牵手服务器（[hysteria-realm-server](https://github.com/apernet/hysteria-realm-server)），自建时需设置强密码

##### 客户端配置示例

```yaml
server: realm://public@realm.hy2.io/your-realm-name
auth: your-hysteria-password
tls:
  sni: your-domain.com
  insecure: true
transport:
  type: udp
socks5:
  listen: 127.0.0.1:20808
```

> 详情参考：[Hysteria 2 Realms 官方文档](https://hysteria.network/zh/docs/advanced/Realms/)
