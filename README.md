# AI API Gateway Notes

记录 AI 编码工具（Claude Code / Codex CLI / Cherry Studio）接入统一 API 网关的配置与踩坑。

**统一端点**

```
https://api.dshapi.icu/v1
```

兼容 OpenAI + Anthropic 双协议，国内直连，按量计费。

## 📘 配置指南

**[→ 完整配置教程（在线）](https://1261398983.github.io/ai-api-guide/)**

覆盖工具：

- Claude Code —— 改 `ANTHROPIC_BASE_URL`
- Codex CLI —— 改 `OPENAI_BASE_URL` 或写 `~/.codex/config.toml`
- Cherry Studio / NextChat / LobeChat —— 填自定义端点
- Python / Node.js / curl —— 换 `base_url` 即可

## 📂 相关仓库

- [ai-api-guide](https://github.com/1261398983/ai-api-guide) —— 在线配置指南（GitHub Pages）
- [dsh-api-quickstart](https://github.com/1261398983/dsh-api-quickstart) —— 6 种工具的完整配置示例

## ⚡ 快速开始

```bash
# Claude Code
export ANTHROPIC_BASE_URL="https://api.dshapi.icu/v1"
export ANTHROPIC_AUTH_TOKEN="你的Key"

# Codex CLI
export OPENAI_BASE_URL="https://api.dshapi.icu/v1"
export OPENAI_API_KEY="你的Key"
```

## 选站 Checklist

- [ ] 双协议兼容（OpenAI + Anthropic）
- [ ] 按量计费，余额不过期
- [ ] 后台有用量明细
- [ ] 支付方式本地化
- [ ] 注册门槛低（无需海外信用卡）

---

价格与模型可用性以平台后台实际展示为准。
