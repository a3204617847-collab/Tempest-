# 创业人生 🚀 部署指南

## 一键部署到 Vercel（5分钟搞定）

### 第1步：准备 DeepSeek API Key
1. 打开 https://platform.deepseek.com
2. 注册账号（国内手机号即可）
3. 在控制台创建 API Key，复制保存

### 第2步：上传到 GitHub
1. 登录 GitHub，点右上角 `+` → `New repository`
2. 仓库名填 `startup-life`，选 Public，点 Create
3. 把本项目所有文件上传到仓库（拖拽上传即可）

项目结构应该是：
```
startup-life/
├── api/
│   └── chat.js          ← API代理（解决跨域）
├── public/
│   └── index.html       ← 游戏主页面
├── vercel.json          ← Vercel配置
├── package.json
└── README.md
```

### 第3步：部署到 Vercel
1. 打开 https://vercel.com，用 GitHub 账号登录
2. 点 `Add New` → `Project`
3. 找到刚才的 `startup-life` 仓库，点 `Import`
4. **重要！** 点开 `Environment Variables`，添加：
   - Key: `DEEPSEEK_API_KEY`
   - Value: （粘贴你的 DeepSeek API Key）
5. 点 `Deploy`，等1分钟

### 第4步：完成！
部署成功后会给你一个地址，类似：
`https://startup-life-xxxxx.vercel.app`

这个链接发给任何人都能直接玩！

## 常见问题

**Q: 国内能访问吗？**
A: Vercel的 .vercel.app 域名在大陆部分地区可能会慢，如果不稳定可以绑定自己的已备案域名。

**Q: API费用多少？**
A: DeepSeek 非常便宜，每百万token输出约 ¥3。一局游戏约几千token，成本不到1分钱。

**Q: 怎么绑自己的域名？**
A: 在 Vercel 项目 Settings → Domains 添加你的域名，然后在域名服务商那边添加 CNAME 记录。

**Q: API调用失败怎么办？**
A: 游戏有内置的高质量备用事件池，即使API失败也能正常玩。检查 Vercel 的 Function Logs 看具体错误。
