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
    - 1. ```git pull```                     先拉取最新版本，避免版本衝突
    - 2. ```git switch -c feat/功能名稱```   建立並切換到一個新功能分支
    - 3. ```git add` 與 `git commit```      編輯 與 提交 程式碼
    - 4. ```git push origin feat/功能名稱``` 將分支推送到遠端倉庫
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

## Git克隆GitHub遠端專案
- 如果已有 GitHub 倉庫，可用 git clone 將遠端專案複製到本地
>使用 HTTPS（適合大多數網路環境）：
>`git clone https://github.com/用戶名/倉庫名.git`
>
>使用 SSH（需先設定 SSH 金鑰）：
>`git clone git@github.com:用戶名/倉庫名.git`

---

## Git本地連接GitHub倉庫操作
- 完成本地版本控制後推送到 GitHub 進行遠端管理或分享
>綁定遠端倉庫，<URL> 替換為 GitHub 專案的 URL
>`git remote add origin <URL>`
>
>檢查遠端倉庫連結是否正確
>`git remote -v`
>
>推送當前分支（預設 main）到遠端並設為預設追蹤分支
>`git push -u origin main`
>
>後續提交直接推送更新到遠端
>`git push`
>
>拉取遠端最新版本並合併，避免衝突
>`git pull`

---

## Git初始設定
- 在開始使用 Git 之前，建議先設定使用者資訊，這些資訊會附加到每次提交中，方便追蹤修改的來源
> 設定全域的使用者名稱，讓 Git 知道提交是由誰執行的
>`git config --global user.name "你的名稱"`
> 
> 設定全域的電子郵件地址，通常使用與 GitHub 帳戶相關聯的 Email，便於身份驗證和追蹤
>`git config --global user.email "你的Email"`
> 
> 設定初始化 Git 倉庫時的預設分支名稱為 main，現代專案通常使用 main 而非舊版的 master
>`git config --global init.defaultBranch main`
> 
> 設定 VSCode 作為 Git 的預設文字編輯器，--wait 參數確保編輯完成後才返回 Git
>`git config --global core.editor "code --wait"`

### 注意
- 如果使用 SSH 方式連接 GitHub，需要先在本地產生金鑰，並將金鑰內容複製到 GitHub 帳戶的 SSH Keys 設定中
>生成 SSH 金鑰，-t 指定密鑰類型（這裡使用 ed25519 為較安全的選擇），-C 則用來備註 Email 資訊
>`ssh-keygen -t ed25519 -C "your_email@example.com"`
>完成後，將 `~/.ssh/id_ed25519.pub` 檔案中的內容貼到 GitHub 的 SSH Keys 頁面

---

## 初始化與版本控制
- 當進入新專案時，需初始化 Git 倉庫並將檔案加入版本控制
>初始化 Git 倉庫，建立 .git 子目錄
>`git init`
>
>查看工作目錄狀態，顯示修改或新增的檔案
>`git status`
>
>將所有改動加入暫存區，或指定檔案（如 index.html）
>`git add . `
>`git add <檔名>`
>
>提交暫存區變更到版本庫，-m 後附提交訊息描述更動
>`git commit -m "提交訊息"`
>
>查看提交記錄，按時間反序列出所有 commit
>`git log`
>
>檢查未加入暫存區或未提交的修改差異
>`git diff`

---

## 分支管理
- 分支可以讓多人同時開發多個功能，並且保持主分支的穩定性，分支合併後可增加工作流程的靈活性
>查看本地所有分支，當前分支會標記 *
>`git branch`
>
>建立本地新分支但不切換
>`git branch <分支名>`
>
>切換分支（推薦使用 switch）
>`git switch <分支名>`
>
>切換分支（舊版或習慣用法）
>`git checkout <分支名>`
>
>建立並切換到新分支
>`git switch -c <新分支名>`
>
>合併其他分支到當前分支
>`git merge <分支名>`
>
>刪除本地已完成的分支
>`git branch -d <分支名>`

### 遠端分支操作
- 遠端分支操作主要用於與遠程倉庫同步與維護分支，方便與團隊成員進行協作
>取得遠端更新但不合併
>`git fetch`
>
>拉取遠端更新並合併到當前分支
>`git pull`
>
>推送本地分支到遠端（建立或更新）
>`git push origin <分支名>`
>
>刪除遠端分支
>`git push origin --delete <分支名>`

---

## 常見錯誤與修復指令
- 使用 Git 時常見的錯誤與修復指令
>更新遠端倉庫 URL（遠端地址變更時使用）
>`git remote set-url origin <新URL>`
>
>暫存未提交的修改（方便切換分支或解決衝突後繼續工作）
>`git stash`
>
>還原剛剛暫存的修改到工作目錄
>`git stash pop`
>
>遇到 git pull rebase 衝突時，臨時關閉 rebase
>`git config pull.rebase false`

---

## 狀態與歷史控制
- 在編輯過程中，有時需要回退或還原更改，Git 提供多種方式應對
>還原工作目錄中某檔案的修改，不影響暫存區
>`git restore <檔案>`
>
>還原已加入暫存區的檔案，重置為最近一次 commit 的狀態
>`git restore --staged <檔案>`
>
>回退 HEAD 到上一個 commit，保留暫存區改動以便修正後重新提交
>`git reset --soft HEAD^`
>
>回退 HEAD 並重置暫存區，取消上次 commit 並將檔案設為未暫存
>`git reset --mixed HEAD^`
>
>強制回退 HEAD 到上一個 commit，丟棄所有修改（謹慎使用）
>`git reset --hard HEAD^`
>
>建立新 commit 撤銷指定 commit 的更改，不改寫歷史（適合已推送的情況）
>`git revert <commit>`

---

## 額外技巧
- 更方便管理 commit 歷史與分支
>簡潔圖形顯示 commit 歷史，快速理解分支與合併
>`git log --oneline --graph --all`
>
>刪除未追蹤的檔案與資料夾，請謹慎使用
>`git clean -fd`
>
>將指定 commit 引入當前分支，適合快速應用單一修正
>`git cherry-pick <commit>`

---

## 忽略檔案設定
- 建立一個 .gitignore 檔案可以讓 Git 忽略掉不想加入版本控制的檔案或資料夾，這對於敏感資料或自動生成的檔案特別有用
>忽略所有 .log 檔案
>`*.log`
>
>忽略 cache 資料夾
>`/cache/`
>
>忽略 VSCode 個人設定檔
>`.vscode/`

###### - 希望這份更詳細的指南能幫助所有初學者更深入地理解 Git 與 GitHub 的操作