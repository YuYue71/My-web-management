---
title: gitHub與Git的大致簡單使用教學
date: 2025-07-27 17-00-00
tags: [GitHub,Git,教學]
---

## Git & GitHub 使用指南
- 適用於初學者與進階開發者，完整涵蓋日常開發常用 Git 指令與 GitHub 操作！

### 推薦 VSCode Git 插件
- 使用 VSCode 時，這些插件可以大幅提升 Git 相關操作的視覺化與便利性:
    - GitLens：增強版 Git 功能，提供詳細的 commit、作者資訊與文件歷史視圖。
    - GitHub Copilot：利用 AI 輔助撰寫程式碼，不過需要單獨訂閱及設定。
    - Git Graph：直觀展示分支與合併歷史，利於視覺化管理版本控制。

### 推薦 GitHub 安全設置
- 為了保護專案，建議採取以下安全措施:
    - 使用 SSH 金鑰登入：避免用密碼，能更安全地連接 GitHub。
    - 開啟兩步驟驗證 (2FA)：即使密碼洩漏，也可加一道防線保護帳戶。
    - 避免直接推送到 main 分支：使用 Pull Request (PR) 流程進行代碼審查，降低錯誤風險。

### 推薦開發流程（Workflow）
- 以下是一個常見的工作流程，從更新專案、建立新分支，到最後合併進主分支的步驟:
    - 1. `git pull`                     先拉取最新版本，避免版本衝突
    - 2. `git switch -c feat/功能名稱`   建立並切換到一個新功能分支
    - 3. `git add` 與 `git commit`      編輯 與 提交 程式碼
    - 4. `git push origin feat/功能名稱` 將分支推送到遠端倉庫
    - 5. 在 GitHub 建立 PR，審查程式碼後合併到 main 分支
    - 6. 合併完成後更新本地 main，並繼續其他開發工作

### 附加資源
- 這些資源可以幫助初學者進一步深入瞭解 Git 與 GitHub 的知識：
    - [Git 官方教學](<https://git-scm.com/doc>)
    - [GitHub Docs](<https://docs.github.com/>)
    - [Pro Git 書籍（繁體）](<https://git-scm.com/book/zh-tw/v2>)

---
---

# 以下是較為詳細Git指令集

## Git初始設定
> 設定全域的使用者名稱，讓 Git 知道提交是由誰執行的
>`git config --global user.name "你的名稱"`

> 設定全域的電子郵件地址，通常使用與 GitHub 帳戶相關聯的 Email，便於身份驗證和追蹤
>`git config --global user.email "你的Email"`

> 設定初始化 Git 倉庫時的預設分支名稱為 main，現代專案通常使用 main 而非舊版的 master
>`git config --global init.defaultBranch main`

> 設定 VSCode 作為 Git 的預設文字編輯器，--wait 參數確保編輯完成後才返回 Git
>`git config --global core.editor "code --wait"`

###### - 希望這份更詳細的指南能幫助所有初學者更深入地理解 Git 與 GitHub 的操作