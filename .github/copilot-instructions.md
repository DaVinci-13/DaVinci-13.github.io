# 项目说明

## 项目背景
本仓库是一个 Hugo 站点，主题使用 `ananke` Git 子模块。
本项目是仓库所有者的个人技术博客。
大多数站点级修改应优先在仓库根目录完成，例如 `content/`、`hugo.toml`，以及根目录下用于覆盖主题行为的 `layouts/`、`assets/`、`static/`、`i18n/`。

## Copilot Chat 交互要求
- 除非用户明确要求其他语言，否则所有问答、解释、总结、方案说明和追问一律使用中文。
- 在起草或修改博客内容时，默认使用中文；只有在用户明确要求英文或双语时才切换。
- 回答应优先结合本仓库的真实结构、现有配置和已存在内容，不要脱离项目上下文给出泛化建议。

## 作者背景与学习方向
- 已具备经验：Unity 游戏开发。
- 正在学习：Unreal 游戏开发、技术美术相关知识。
- 计划深入：AI Agent 在实际工作中的应用、AI 开发、面向游戏技术美术的 DCC 工具链、OpenGL、游戏服务器开发。
- 当需要提出文章选题、示例、标签、分类、站点结构建议或后续工作建议时，优先围绕以上背景与方向展开。

## 构建与验证
本项目本地常用命令如下：

- 本地预览：`hugo server`
- 生产构建：`hugo --gc --minify`
- 如需处理主题相关 JS/CSS 工具链：`cd themes/ananke && npm install`

CI 参考构建流程定义在 `.github/workflows/hugo.yaml`，使用 Hugo extended 并带 `--gc --minify` 参数。

## 架构边界
处理本仓库时按以下边界理解：

- 可直接编辑的站点内容：`content/**`、`hugo.toml`、`archetypes/**`
- 站点级覆盖目录：`layouts/**`、`assets/**`、`static/**`、`i18n/**`
- 主题源码目录：`themes/ananke/**`，仅在明确需要修改主题子模块时才改动
- 生成产物或缓存目录：`public/**`、`resources/_gen/**`、`.hugo_build.lock`，不要手动编辑

如需调整主题行为，优先通过根目录下的 Hugo 覆盖目录实现，而不是直接修改主题文件。

## 内容规范
新增或修改文章时遵循以下约定：

- 使用 TOML front matter，分隔符为 `+++`，格式与 `archetypes/default.md` 保持一致。
- 保留必要字段：`title`、`date`、`draft`。
- 当填写具体日期时，使用带时区的 ISO 时间格式，示例可参考 `content/posts/my-first-post.md`。
- 只有在文章明确准备发布时，才将 `draft = false`。

## Agent 工作约定
- 所有改动应尽量小且聚焦当前需求，避免顺手修改无关内容。
- 不要修改 `public/` 与 `resources/_gen/` 下的生成文件。
- 若需求涉及 `themes/ananke/` 内部实现，最终说明中应明确提示这会影响 Git 子模块。
- 若主题文档中已经说明相关行为，优先引用文档，不重复抄写大段说明。

## 文档参考
以下路径可作为本项目相关工作的主要参考资料：

- 主题概览与功能：`themes/ananke/README.md`
- 主题贡献流程与本地检查：`themes/ananke/CONTRIBUTING.md`
- 主题文档入口：`themes/ananke/docs/_index.md`
- 主题配置文档：`themes/ananke/docs/configuration/`
- 主题内容与 front matter 文档：`themes/ananke/docs/content/`
- 主题自定义文档：`themes/ananke/docs/customisation/`
- CI 构建与部署流程：`.github/workflows/hugo.yaml`
