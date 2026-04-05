<!-- Copyright 2026 Hubbertt. All Rights Reserved. -->

# QuizDocx

## English

`QuizDocx` is a quiz-oriented DOCX import and query plugin for Unreal Engine.

It focuses on turning structured Word documents into stable quiz data, with
config-driven field extraction, cache support, and editor-side pickers for the
most common query inputs.

### Modules

- `QuizDocxRuntime`: import pipeline, schema resolution, cache handling, and query-facing runtime types
- `QuizDocxEditor`: project settings customization, graph pin pickers, and editor bootstrap helpers

### Public Integration Surface

- `UQuizDocxBlueprintLibrary`
- `UQuizDocxSettings`
- `UQuizDocxConfigAsset`
- `FQuizDocxResolvedConfig`

### Scope

This plugin is responsible for:

- reading DOCX quiz sources
- extracting configured fields and dimensions
- caching imported source files
- exposing editor pickers and project defaults for the import workflow

This plugin is not intended to provide:

- a general-purpose word processor bridge
- bundled font rendering or text layout engines
- repository-level localization assets outside this plugin root

### Packaging Guidance

The formal deliverable is the `QuizDocx` plugin root only.

Keep `Source/...`, `README.md`, `LICENSE`, `ThirdPartyNotices.txt`, and
`Config/FilterPlugin.ini`.

This plugin currently ships no bundled font binaries and no standalone
third-party binaries under its own root.

### Platform Notes

- `QuizDocxRuntime` is currently wired for `Win64`, `Mac`, `IOS`, and `Android` in the descriptor so the plugin can participate in cross-platform project builds and packaging.
- `Win64` and `Android` remain the currently re-validated runtime targets in this repository.
- The Android runtime path now builds from source with the vendored `miniz` ZIP reader instead of relying on Unreal's desktop-only `libzip` module.
- `QuizDocxEditor` remains editor-only and is not part of mobile runtime packaging.
- `Mac` and `IOS` are kept enabled for project compilation/package workflows, but they are not yet described here as a separate marketplace-style validation promise.

### Legal Files

- Descriptor: `QuizDocx.uplugin`
- Packaging filter: `Config/FilterPlugin.ini`
- License: `LICENSE`
- Third-party notices: `ThirdPartyNotices.txt`

## 中文

`QuizDocx` 是一个面向题库导入与查询流程的 Unreal Engine DOCX 插件。

它的重点是把结构化 Word 文档稳定转换为题库数据，并提供基于配置的字段抽取、
缓存支持，以及面向编辑器常用查询输入的选择器。

### 模块

- `QuizDocxRuntime`：导入管线、Schema 解析、缓存处理与查询侧运行时类型
- `QuizDocxEditor`：项目设置定制、图引脚选择器与编辑器启动辅助

### 对外公开接口

- `UQuizDocxBlueprintLibrary`
- `UQuizDocxSettings`
- `UQuizDocxConfigAsset`
- `FQuizDocxResolvedConfig`

### 职责边界

本插件负责：

- 读取 DOCX 题库源文件
- 按配置抽取字段与维度
- 缓存导入源文件
- 为导入工作流提供编辑器选择器与项目默认值

本插件不负责：

- 通用型文字处理器桥接
- 自带字体渲染或排版引擎
- 继续维护插件根目录外的本地化资产体系

### 打包建议

正式交付物只包含 `QuizDocx` 插件根目录本身。

正式发版时保留 `Source/...`、`README.md`、`LICENSE`、
`ThirdPartyNotices.txt` 与 `Config/FilterPlugin.ini`。

当前插件根目录内不随包分发字体二进制，也不单独附带第三方二进制。

### 平台说明

- `QuizDocxRuntime` 当前已在描述文件中对 `Win64`、`Mac`、`IOS`、`Android` 开放，使插件能够参与项目级跨平台编译与打包。
- `Win64` 与 `Android` 仍然是本仓库里已经重新完成验证的运行时目标。
- Android 运行时链路现在基于随源码分发的 `miniz` ZIP 读取实现构建，不再依赖 Unreal 自带且偏桌面平台的 `libzip` 模块。
- `QuizDocxEditor` 仍然是纯编辑器模块，不属于移动端运行时打包范围。
- `Mac`、`IOS` 目前保留为项目编译/打包可用目标，但这里暂不把它们写成独立的 marketplace 式正式验证承诺。

### 法律文件

- 描述文件：`QuizDocx.uplugin`
- 打包过滤规则：`Config/FilterPlugin.ini`
- 许可证：`LICENSE`
- 第三方声明：`ThirdPartyNotices.txt`
