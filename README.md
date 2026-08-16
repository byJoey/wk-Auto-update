# 是读写权限     不是读取存储权限   视频错了



## 🚀 快速开始（适合 Fork）

1. 点击右上角 Fork 本仓库到你的 GitHub 账号。

2. 打开你的仓库，进入 Actions 页面，点击 Enable workflows（启用 GitHub Actions）。

3. 无需其他配置，GitHub 默认的 GITHUB_TOKEN 权限即可推送更新。

4. 你可以手动点击 Run workflow，也可以等待每天定时自动检查。

> 注意：确保你的仓库默认分支为 main，否则推送时可能失败。

🌟 如果觉得这个项目对你有帮助，欢迎顺手点个 Star 支持一下！

## 功能介绍

* 每天自动检查 bia-pain-bache/BPB-Worker-Panel 仓库的最新 Release

* **支持选择更新正式版或预发布版本：通过手动触发或 `update_type.txt` 文件配置 1是正式版 0是测试版本。**

* 自动下载最新版本的 worker.js

* 重命名为 \_worker.js

* 同步更新本地 version.txt

* 自动提交并推送到本仓库

* **如果 `update_type.txt` 文件不存在，将自动创建并默认设置为更新正式版。**

* **更新成功后，自动复用或创建 GitHub Issue 进行通知。**

## 工作流程

GitHub Actions 会每日 00:00（UTC 时间）自动运行：

1. **检查 `update_type.txt` 文件：如果文件不存在，会自动创建并写入 `1`（表示正式版）。**

2. **根据 `update_type.txt` 或手动输入确定更新类型（正式版或预发布版）。**

3. 获取上游仓库的最新 Release 版本号（根据所选类型）。

4. 比较本地 version.txt 的记录。

5. 若版本不同，则自动下载并替换 \_worker.js。

6. 更新 version.txt。

7. 自动提交并推送到主分支（main）。

8. **如果 `update_type.txt` 文件是自动创建的，也会一并提交到仓库。**

9. **如果更新成功并提交了更改，工作流会首先查找一个名为 `_worker.js 自动更新通知` 且带有 `auto-update-status-issue` 标签的现有 Issue。如果找到，则在该 Issue 下添加一条评论，包含更新时间、版本类型和版本号；如果未找到，则创建一个新的 Issue 并添加该标签。**

> 若版本一致，则不执行任何操作。

## 📂 目录结构

/
├── \_worker.js
├── version.txt
├── **update_type.txt**
├── LICENSE
├── .gitignore
├── README.md
└── .github/
    └── workflows/
        └── update_worker.yml

## ⚙️ 配置说明

* 无需手动设置 Token：默认使用 GitHub 提供的 GITHUB_TOKEN 进行权限认证。

* 如需修改同步源：编辑 .github/workflows/update_worker.yml，修改源仓库地址即可。

* **更新类型配置（`update_type.txt`）：**

  * 在仓库根目录下创建或修改 `update_type.txt` 文件。

  * 文件内容为 `1`：表示定时任务将更新到**最新正式发布版本**。

  * 文件内容为 `0`：表示定时任务将更新到**最新预发布版本**。

  * **如果 `update_type.txt` 文件不存在，工作流会自动创建它并默认设置为 `1`（正式版）。**

  * **手动触发时，您可以通过 GitHub Actions 界面选择更新类型，此选择将覆盖 `update_type.txt` 的设置。**

* **更新成功通知：**

  * 工作流在成功更新并提交代码后，会尝试复用一个特定的 GitHub Issue 进行通知。

  * 该 Issue 的标题统一为 `_worker.js 自动更新通知`，并带有 `auto-update-status-issue` 标签。

  * 如果该 Issue 已存在，新的更新信息将作为评论添加到该 Issue 中，这样可以保持通知集中在一个地方。

  * 如果该 Issue 不存在，工作流会创建一个新的 Issue。

  * 您可以通过关注该仓库的 Issue 动态来接收通知。

## 📜 开源协议

本项目使用 MIT License 开源。

您可以自由地使用、复制、修改和分发本项目，前提是附带原始许可证声明。

## 🌐 社区与交流

如果有任何问题或建议，欢迎加入我们的 Telegram 群组交流：

👉 加入 Telegram 群组：<https://t.me/+ft-zI76oovgwNmRh>

## 📢 特别说明

* 本仓库同步的内容来源于 [BPB-Worker-Panel](https://github.com/bia-pain-bache/BPB-Worker-Panel)。

* 原项目版权归原作者所有，本项目仅用于自动同步更新，不对原内容进行修改。

## Star Histor

## Star History

[![Star History Chart](https://star-history.dera.page/svg?repos=byJoey/wk-Auto-update&type=Timeline)](https://star-history.dera.page/#byJoey/wk-Auto-update&Timeline)

