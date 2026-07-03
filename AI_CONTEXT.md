# AI Context

## 项目概述
本项目是酒馆角色卡远程卡库，托管在 GitHub 仓库 `emo-lsp/st-character-catalog`。核心资源包括角色卡 PNG、Markdown 简介和根目录 `cards.json` 清单，前端通过 GitHub Raw 地址读取。

## 当前状态
仓库已在本地维护多个角色卡条目，新增或更新角色时需要同步资源文件与 `cards.json`，并保证公开地址指向 `main` 分支 Raw 资源。

## 最近变更
- 2026-07-04 更新 `妻悦论坛` 至 1.8.1，新增 `cards/qi-yue-lun-tan-1.8.1.png`，更新 `cards.json` 版本、Raw 地址和更新日志
- 2026-05-20 新增 `洛雪棠` 角色卡上传流程，涉及 `cards/`、`intros/`、`cards.json`

## 项目结构
cards/
├── `id-version.png` 角色卡资源，供酒馆导入

intros/
├── `id.md` 角色简介 Markdown，前端详情页直接渲染

covers/
├── 可选独立封面图；未提供时前端会从角色卡生成 JPEG 预览

cards.json
角色卡远程清单，前端固定读取此文件中的公开 Raw 地址

## 架构与关键决策
- `cardUrl`、`introUrl`、`coverUrl` 必须使用 `raw.githubusercontent.com` 地址，不能使用 GitHub `blob` 页面。
- `publishedAt` 只能由用户手动指定，不能自动生成。
- 用户未手动指定“最后更新”时，`updatedAt` 必须取对应角色卡 PNG 的最近一次 Git 提交时间。
- 更新清单时保留既有条目和字段，不做无关重排或无关重构。

## 已知问题 / TODO
- [ ] `.DS_Store` 仍存在于仓库工作区，当前上传流程不处理该无关文件。

## 新对话快速上手
先读根目录 `cards.json` 和本文件，再按 `cards/`、`intros/` 的现有命名规则新增或更新角色。若用户要求“现在发布”，要把具体时间写入 `publishedAt`，不要写模糊表述。
