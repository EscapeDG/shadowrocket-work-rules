# Shadowrocket 工作应用分流规则

用于 iPhone / iPad 上的 Shadowrocket，为 Microsoft Teams、LinkedIn、WhatsApp 和 Microsoft Copilot 的相关流量选择代理。

## 使用方法

1. 备份现有配置，打开 [Work.conf](Work.conf)，将其中规则加入现有配置的 `[Rule]` 段，放在宽泛直连规则和 `FINAL` 之前。
2. `PROXY` 使用现有配置中有效的代理策略；如果你的配置使用其他策略名称，请相应替换。
3. 首页的全局路由选择「配置」，连接节点，分别测试登录、消息、通话、会议和文件功能。

`Work.conf` 是配置片段，不是完整配置文件；不会指定其他流量的默认策略。远程规则集需要设备能够访问 GitHub 的原始文件地址，更新取决于上游，并非由本仓库自动维护。

## 范围和注意事项

规则按目标域名和 IP 匹配，不按 App 身份匹配。上游 WhatsApp 和 Copilot 规则包含共享域名及 IP / ASN 范围，其他服务也可能命中。Microsoft 365 登录、文件及会议依赖共享服务，这些规则不保证所有功能均可用；如遇问题，请检查连接日志并按需添加规则。涉及公司设备和账号时遵循组织的网络与安全策略。

## 来源

- [blackmatrix7/ios_rule_script：Shadowrocket 规则](https://github.com/blackmatrix7/ios_rule_script/tree/master/rule/Shadowrocket)，本配置以远程 RULE-SET 引用，不复制上游列表。
- [Microsoft 365 服务端点](https://learn.microsoft.com/en-us/microsoft-365/enterprise/urls-and-ip-address-ranges?view=o365-worldwide)
- [Microsoft Copilot 网络要求](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-copilot-requirements)
