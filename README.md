# AI API Gateway Notes

记录 AI 编码工具（[CC] / Codex CLI / Cherry Studio）接入统一 API 网关的配置与踩坑。

**统一端点**

```
https://api.97wl.cc/v1
```

兼容 [OI] + Anthropic 双协议，国内直连，按量计费。

注册只需 QQ 邮箱，无需邀请码、无需外币卡：**[→ 打开站点](https://api.97wl.cc/register)**

## 📘 配置指南

**[→ 完整配置教程（在线）](https://1261398983.github.io/ai-api-guide/)**

覆盖工具：

- [CC] —— 改 `ANTHROPIC_BASE_URL`
- Codex CLI —— 改 `OPENAI_BASE_URL` 或写 `~/.codex/config.toml`
- Cherry Studio / NextChat / LobeChat —— 填自定义端点
- Python / Node.js / curl —— 换 `base_url` 即可

## 🔍 排障与实测

- **[连不上？四层排查](https://1261398983.github.io/ai-api-guide/why-blocked.html)** —— DNS / TLS / 鉴权 / 出口，每层给判据与命令
- **[错误码完全对照表](https://1261398983.github.io/ai-api-guide/errors.html)** —— 401 / 402 / 429 / 500 逐个定位
- **[8 家中转站延迟实测](https://1261398983.github.io/ai-api-guide/uptime.html)** —— 同机 5 次采样，原始样本公开

## 🧭 决策参考

- **[中转站怎么选](https://1261398983.github.io/ai-api-guide/choosing-relay.html)** —— 6 条判断标准 + 5 个 60 秒验证动作
- **[跑路前兆与资金安全](https://1261398983.github.io/ai-api-guide/risk.html)** —— 7 个可查信号 + 止损步骤
- **[成本对照](https://1261398983.github.io/ai-api-guide/cost-compare.html)** —— 倍率不等于折扣，含汇率与重试损耗
- **[能开发票吗](https://1261398983.github.io/ai-api-guide/invoice.html)** —— 企业采购与报销的四条路径
- **[团队 Key 管理](https://1261398983.github.io/ai-api-guide/team-keys.html)** —— 共用一把 key 的四个坑

## 📂 相关仓库

### 配置与接入

- [ai-api-guide](https://github.com/1261398983/ai-api-guide) —— 在线配置指南（GitHub Pages）
- [ai-api-quickstart](https://github.com/1261398983/ai-api-quickstart) —— 6 种工具的完整配置示例

### 中转站导航

- [ai-relay](https://github.com/1261398983/ai-relay) —— 实测可用的 AI 公益站清单
- [ai-welfare-hub](https://github.com/1261398983/ai-welfare-hub) —— [CC] 免费额度与公益站导航
- [ai-coding-welfare](https://github.com/1261398983/ai-coding-welfare) —— AI Coding 福利站合集
- [ai-api-relay-directory](https://github.com/1261398983/ai-api-relay-directory) —— 中转站倍率对照表（每日同步）
- [ai-api-zhongzhuan](https://github.com/1261398983/ai-api-zhongzhuan) —— 中转站公开目录
- [ai-relay-nav](https://github.com/1261398983/ai-relay-nav) —— 公益站 / 中转站推荐

### Awesome 清单

- [awesome-ai-api-relay](https://github.com/1261398983/awesome-ai-api-relay) —— AI API 中转服务精选
- [awesome-ai-coding-tools](https://github.com/1261398983/awesome-ai-coding-tools) —— AI 编程工具精选
- [awesome-chinese-ai-tools](https://github.com/1261398983/awesome-chinese-ai-tools) —— 中文 Agent Skills 合集

## ⚡ 快速开始

```bash
# [CC] —— 注意 base_url 不带 /v1
export ANTHROPIC_BASE_URL="https://api.97wl.cc"
export ANTHROPIC_AUTH_TOKEN="你的Key"

# Codex CLI / [OI] 兼容客户端 —— 要带 /v1
export OPENAI_BASE_URL="https://api.97wl.cc/v1"
export OPENAI_API_KEY="你的Key"
```

**两个最高频的坑：**

1. `[CC]` 认的是 `ANTHROPIC_AUTH_TOKEN`，不是 `ANTHROPIC_API_KEY`。写错就是 401。
2. `base_url` 带不带 `/v1` 取决于走哪种协议。`[CC]` 不带，`[OI]` 兼容要带。这是最高频的 404 原因。

## 选站 Checklist

- [ ] 双协议兼容（[OI] + Anthropic）
- [ ] 按量计费，输入输出分开计价，倍率公开
- [ ] 后台有用量明细，可查每次调用 token 数
- [ ] 面板开源（Sub2API / NewAPI），计费可审计
- [ ] 支付方式本地化
- [ ] 注册门槛低（无需海外信用卡）
- [ ] 起充门槛低，可以先小额试

---

## 说明

个人部署的第三方 API 转发服务，非上游厂商官方产品。建议按实际用量充值，避免一次性大额预付；重要业务请自备备份线路。

价格与模型可用性以平台后台实际展示为准。
