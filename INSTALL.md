# 安装与分发

将压缩包中的 `xiumi-layout` 整个目录复制到目标 agent 的技能目录，保留子目录结构。不要只复制 SKILL.md。

## Codex

默认目录为 `~/.codex/skills/xiumi-layout/`；若设置了 CODEX_HOME，则使用其下的 `skills/xiumi-layout/`。已有同名技能时先备份，并检查本地自定义规则后再替换。安装后重新打开会话或按宿主方式刷新技能列表。

调用示例：

> 请使用 $xiumi-layout，在我打开的秀米模板副本上排版这份文稿和配图，完成后检查预览并保存草稿。

## 其他 agent

支持 SKILL.md 的 agent：复制到它自己的技能搜索目录，按其方式加载。`agents/openai.yaml` 是 Codex 的可选显示元数据，其他宿主可忽略。

不支持技能自动发现的 agent：明确要求它读取 SKILL.md，并在实际操作前读取 references/ui-operations.md。所有相对链接均相对于当前文件。

## 依赖与默认规则

- 浏览器操作指定使用 BrowserSkill（github.com/Tencent/BrowserSkill，MIT 许可，`bsk` CLI + Chrome/Edge 扩展）和已登录秀米的浏览器。本包不安装控制工具、不包含登录信息。BrowserSkill 以 shell 命令工作并在用户真实浏览器中执行，跨 agent 行为一致；安装方式见其仓库（`install.sh` + `bsk install-skill`），文件上传下载仅本地模式可用。
- 原稿和配图需在每次任务中单独提供，本包不含文章、二维码或个人路径。
- 现有配色、留白及署名规则保留为默认方案。软件学院审核名单属于原维护者的组织配置，使用前核实组织与名单是否仍适用；其他组织不套用。
- 《推送模板表》（`references/推送模板表.xlsx` + `references/推送模板表-速查.md`）随本包分发，属于账号本地配置的快照；扫描脚本仍在排版工作区，不随包分发。表过期或缺失时按 skill 的降级顺序执行（当次指定模板 > 询问用户 > 无模板从头排版）。
- 用户指定的样式、操作方式和任务范围优先。仅要求保存草稿时不同步，更不发布。
- 本包已检查文件结构和引用；没有在真实秀米页面重新执行排版测试。
