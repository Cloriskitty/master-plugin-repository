# master-plugin-repository

**OKX 内部 Claude Code 插件市场** —— OKX 内部黑客松的官方插件提交入口。

> English version: [README.md](./README.md)

## 这是什么

一个 Claude Code 插件市场（marketplace）。添加该市场后，黑客松提交的每一个插件都会出现在 Claude Code 的 `/plugin` 界面中，参与者和评审可以一键安装。

## 面向谁

仅限获得授权的 OKX 员工和黑客松参赛者。使用受 [LICENSE](./LICENSE) 约束 —— 保密、仅限内部使用，未经 OKX 法务书面同意不得外传。

## 将该市场添加到 Claude Code

在任意 Claude Code 会话中执行：

```
/plugin marketplace add mastersamasama/master-plugin-repository
```

然后打开市场面板：

```
/plugin
```

在 **Discover（发现）** 标签页中可以看到已提交的插件。

## 安装插件

从列表中挑选一个插件并执行：

```
/plugin install <plugin-name>@master-plugin-repository
/reload-plugins
```

安装后，该插件附带的 skills / commands 即可在当前会话中使用。

## 提交插件（引导流程）

> **阶段 A（当前）：** 先安装 `test-plugin`，然后用它的 `submit-plugin` skill 发起提交 PR。这是在 `plugin-store-tools` 合入之前的引导路径。
>
> **阶段 B（即将上线）：** 安装 `plugin-store-tools` 获取完整工具链 —— `scaffold-plugin`、`validate-plugin`、`skill-to-plugin`，以及一个调用共享校验器的生产级 `submit-plugin`。

引导步骤：

1. `/plugin marketplace add mastersamasama/master-plugin-repository`
2. `/plugin install test-plugin@master-plugin-repository`
3. `/reload-plugins`
4. `/test-plugin:submit-plugin` —— 交互式流程：询问你的插件目录、进行基础校验、fork 本仓库并开 PR。

支持两种提交模式：
- **external（外部仓库）**：你的插件保存在你自己的仓库中，PR 只往 `marketplace.json` 里加一条指向你仓库的条目。
- **monorepo（单仓库）**：你的插件目录会被复制到本仓库的 `plugins/` 下。

## 仓库结构

```
.claude-plugin/marketplace.json     # 市场目录文件
plugins/test-plugin/                # 引导插件，内含 submit-plugin
LICENSE                             # OKX 专有授权声明
README.md                           # English
README.zh-Hans.md                   # 你正在阅读
```

## 合规声明

本仓库及其中所有插件均为 OKX 机密资产。禁止对外发布、对外 fork 或在 OKX 授权渠道之外分享。提交的插件中不得包含任何密钥、机密 OKX 数据或你不拥有合法使用权的第三方知识产权。完整条款详见 [LICENSE](./LICENSE)。

## 问题反馈

在本仓库提 issue，或通过 OKX 内部渠道联系黑客松组织者。
