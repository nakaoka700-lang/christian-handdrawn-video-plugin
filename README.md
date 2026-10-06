# Christian Hand-Drawn Video for Codex

一个可在 Codex 中复用的中文基督教手绘叙事视频工作流插件。

它将配音、SRT 字幕和可选参考图转化为可编辑的 Remotion 项目，并包含：

- GPT 场景插画与逐张自查；
- 强制用户插画审批门；
- 与配音同步的中文英雄字幕；
- 字幕安全边界、遮挡和语义拆分检查；
- 自然场景运动与转场审计；
- 浏览器预览优先，只有用户明确要求时才导出 MP4；
- 导出完成后才提供需要再次批准的可选磁盘清理流程。

## 安装

在 Codex CLI 中添加本 GitHub 仓库作为插件市场：

```bash
codex plugin marketplace add https://github.com/nakaoka700-lang/christian-handdrawn-video-plugin --ref main
```

然后运行 `/plugins`，选择 `Christian Video Tools`，安装“基督教中文手绘视频”，并新建一个任务。

## 调用

将配音、SRT 字幕和参考图放入同一个工作文件夹，然后输入：

```text
使用 $create-christian-handdrawn-video，根据当前文件夹中的配音、SRT 和参考图制作中文手绘视频。
```

## 依赖

- Codex 或 ChatGPT 桌面版中的 Codex；
- 可用的 ImageGen 能力；
- Remotion 插件/Skills；
- 本机 Node.js 与 npm；
- 足够的磁盘空间保存插画、Remotion 工程和审计帧。

本插件只包含工作流指令，不包含生成的视频、音频、字幕、插画或项目素材。

## License

MIT
