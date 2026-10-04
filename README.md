# nano-chat

一个文件、双击即用的 LLM 聊天客户端。open-webui 的"小巧思"替代版：不要 Docker、不要 npm、不要构建——就一个 `index.html`。

## 为什么不用 open-webui？

| | open-webui | nano-chat |
|---|---|---|
| 启动 | Docker 拉镜像、配端口 | 双击 `index.html` |
| 体积 | 几百 MB 镜像 | 一个 ~30KB 的 HTML |
| 离线可用 | 需要本机服务一直在跑 | 文件本身零外部请求，纯离线打开 |
| 功能 | 完整（RAG、多用户、模型管理…）| 只做一件事：和 OpenAI 兼容接口聊天 |

诚实说明取舍：没有 RAG、没有多用户、没有提示词库，历史记录只存在本机浏览器。如果你要的是"打开就能聊"，nano-chat 够了；要的是团队知识库网关，请继续用 open-webui。

## 使用方法

1. 下载 `index.html`（仓库里就这一个文件是本体）
2. 双击用浏览器打开（Chrome / Edge / Safari / Firefox 均可，`file://` 直接能用）
3. 点右上角 **⚙ 设置**，填三项：
   - **API 地址**：默认 `https://api.openai.com/v1`，兼容任何 OpenAI 格式接口（DeepSeek / Kimi / 硅基流动 / 自建网关…）
   - **API Key**
   - **模型**：默认 `gpt-4o-mini`
4. 点"测试连接"，成功后开始聊天

## 功能列表

- 💬 多对话管理：新建 / 双击重命名 / 删除，全部存 `localStorage`
- 🌊 流式输出：token 逐字渲染，可随时"停止"
- 📝 自带 Markdown 渲染：代码块（带语言标签 + 一键复制）/ 表格 / 引用 / 列表 / 粗斜体 / 链接，代码块内 HTML 自动转义
- 🌐 中英双语界面一键切换
- 🤖 单条回复操作：复制 / 一键翻译（调用当前模型，中文界面译成中文，英文界面译成英文）/ 删除
- 💾 导出：单对话导出 Markdown 文件，全部对话导出 JSON
- 📊 token 估算表：侧栏底部显示当前对话约用 token（字符数 ÷ 4，**估算值非计费口径**）
- 📱 移动端可用：小屏自动收起侧边栏

## 安全说明

- API Key **只保存在本机浏览器的 localStorage**，页面本身不发起除你配置的 API 地址之外的任何网络请求（可用浏览器开发者工具 Network 面板验证）
- 不要把填好 key 的浏览器 profile 或导出的 JSON 发给别人；换电脑使用时在设置里重新填 key 即可

## License

MIT（见 `LICENSE` 文件）
