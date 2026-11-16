# make-knowledge-cards

`make-knowledge-cards` 是一个 Codex Skill，用于把用户粘贴的文章或本地 Markdown、TXT 文件提炼成便于理解和复习的知识卡片。

## 项目解决什么问题

长文章往往混有铺垫、重复表述和次要细节，不方便快速复习。本 Skill 从原文中识别真正重要的定义、机制、关键步骤、判断条件或研究结论，并将它们整理成结构统一的卡片。

每张卡片只讲一个知识点。生成内容严格依据原文，不补充原文没有的信息。文章内容不足时，会按实际可提取的知识点数量输出，不会为了凑数拆分或编造内容。

## 主要功能

- 接收直接粘贴的文章正文。
- 读取本地 `.md`、`.markdown` 和 `.txt` 文件。
- 通常生成 5～8 张知识卡片，材料较短时可以少于 5 张。
- 按重要性筛选知识点，并合并含义相同的重复内容。
- 保留结论所需的适用条件、研究对象、对比范围和不确定性。
- 为每张卡片生成标题、核心知识、简明解释，以及原文例子或可依据原文回答的自测问题。
- 使用 Markdown 输出，便于继续编辑或保存。

当前不支持网页抓取、PDF、Anki 导出和图形界面。

## 安装方法

将 Skill 目录复制到 Codex 的个人 Skills 目录：

```bash
mkdir -p ~/.codex/skills
cp -R skills/make-knowledge-cards ~/.codex/skills/
```

如果目标目录中已经存在同名 Skill，请先自行确认需要保留或替换的版本。安装完成后，在可使用 Skills 的 Codex 会话中调用 `$make-knowledge-cards`。

也可以不安装，直接在当前项目中指定 [SKILL.md](skills/make-knowledge-cards/SKILL.md)，请 Codex 按其中的规则处理文章。

## 使用方法

### 粘贴文章

在 Codex 中输入以下请求，并在后面粘贴文章正文：

```text
请使用 $make-knowledge-cards，把下面这篇文章转化为知识卡片：

<文章正文>
```

### 读取本地文件

提供当前工作区内 Markdown 或 TXT 文件的路径：

```text
请使用 $make-knowledge-cards，把 notes/reading.md 转化为知识卡片。
```

输出为 Markdown。通常包含 5～8 张卡片。如果原文不足以支持 5 个独立知识点，Skill 会说明情况并按实际数量输出。

## 输入输出示例

**输入**

```text
写操作指南时，把前置条件放在步骤之前。读者可以先确认工具和权限齐备，再开始操作。
```

**输出**

```markdown
原文有 1 个可独立复习的知识点，共生成 1 张卡片。

## 操作指南中的前置条件

- **核心知识**：将前置条件放在操作步骤之前。
- **简明解释**：读者能在动手前确认自己是否具备所需工具和权限。
- **自测问题**：为什么应在操作步骤之前列出所需工具和权限？
```

Skill 的完整规则位于 [skills/make-knowledge-cards/SKILL.md](skills/make-knowledge-cards/SKILL.md)。
