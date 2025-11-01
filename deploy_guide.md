# 班級網頁線上部署指南

## 方案一：使用 GitHub Pages（免費）

### 步驟 1：創建 GitHub 帳號
1. 前往 [GitHub](https://github.com/) 註冊一個帳號（如果您還沒有）
2. 登入您的 GitHub 帳號

### 步驟 2：創建新的儲存庫
1. 點擊右上角的 "+" 圖標，選擇 "New repository"
2. 儲存庫名稱輸入：`class-website`（或您喜歡的名稱）
3. 選擇 "Public"（公開）
4. 點擊 "Create repository"

### 步驟 3：上傳網站文件
1. 在您的電腦上安裝 Git（如果尚未安裝）：https://git-scm.com/downloads
2. 打開命令提示字元（CMD）或 PowerShell
3. 執行以下命令：

```bash
# 進入您的網站文件夾
cd c:\Users\a0926\Desktop\影片

# 初始化 Git 儲存庫
git init

# 添加所有文件
git add .

# 提交更改（這一步非常重要，必須先提交才能推送）
git commit -m "Initial commit"

# 如果遇到錯誤提示需要設置用戶名和郵箱，請執行：
# git config --global user.email "your-email@example.com"
# git config --global user.name "Your Name"
# 然後再次提交：
# git commit -m "Initial commit"

# 連接到您的 GitHub 儲存庫（替換 YOUR_USERNAME 為您的 GitHub 用戶名）
# 如果遇到 "error: remote origin already exists" 錯誤，請使用以下命令替換現有的 origin
git remote set-url origin https://github.com/YOUR_USERNAME/class-website.git
# 或者，如果您想使用不同的名稱，可以使用：
# git remote add github https://github.com/YOUR_USERNAME/class-website.git

# 推送文件到 GitHub
# 如果遇到 "error: failed to push some refs" 錯誤，可能是因為遠端儲存庫有您本地沒有的內容
# 先拉取遠端儲存庫的內容
git pull --rebase origin master

# 然後再嘗試推送
git push -u origin master

# 如果仍然有問題，可以嘗試強制推送（謹慎使用，會覆蓋遠端的更改）
# git push -f origin master

# 如果您使用了不同的遠端名稱，請相應調整命令，例如：
# git push -u github master
```

### 步驟 4：啟用 GitHub Pages
1. 在 GitHub 上打開您的儲存庫
2. 點擊 "Settings"
3. 滾動到 "GitHub Pages" 部分
4. 在 "Source" 下拉選單中選擇 "master branch"
5. 點擊 "Save"
6. 等待幾分鐘，您的網站將在 `https://YOUR_USERNAME.github.io/class-website` 上線

## 方案二：使用 Netlify（免費）

### 步驟 1：創建 Netlify 帳號
1. 前往 [Netlify](https://www.netlify.com/) 註冊一個帳號
2. 您可以使用 GitHub、GitLab、Bitbucket 帳號或電子郵件註冊

### 步驟 2：部署網站
1. 登入 Netlify 後，點擊 "New site from Git"
2. 選擇 "Deploy manually"
3. 將您的網站文件夾拖放到上傳區域，或點擊選擇文件夾
4. 等待上傳完成
5. 您的網站將獲得一個隨機的 Netlify 子域名，如 `https://random-name-123456.netlify.app`

### 步驟 3：自訂域名（可選）
1. 在 Netlify 儀表板中，點擊您的網站
2. 點擊 "Domain settings"
3. 點擊 "Add custom domain"
4. 輸入您擁有的域名
5. 按照指示設置 DNS 記錄

## 方案三：使用 000webhost（免費）

### 步驟 1：創建 000webhost 帳號
1. 前往 [000webhost](https://www.000webhost.com/) 註冊一個帳號
2. 登入您的帳號

### 步驟 2：創建新網站
1. 點擊 "Create Website"
2. 輸入網站名稱和密碼
3. 點擊 "Create"

### 步驟 3：上傳網站文件
1. 在儀表板中，點擊 "File Manager"
2. 進入 "public_html" 文件夾
3. 上傳您的 HTML、CSS 和 JavaScript 文件
4. 確保主頁文件名為 "index.html"

### 步驟 4：訪問您的網站
1. 您的網站將在 `https://您的網站名稱.000webhostapp.com` 上線

## 注意事項

1. **後端功能**：目前的網站是靜態的，登入和註冊功能使用的是本地存儲（localStorage）。如果需要真正的用戶管理系統，您需要設置後端服務器和數據庫。

2. **域名**：如果您想要一個專業的域名（如 www.yourschool.com），您需要從域名註冊商購買一個域名，並將其指向您的託管服務。

3. **SSL 證書**：GitHub Pages 和 Netlify 自動提供 HTTPS 支持。如果使用其他服務，您可能需要單獨設置 SSL 證書。

4. **備份**：定期備份您的網站文件和數據庫（如果有）。

5. **更新**：部署後，如果您想更新網站，只需重新上傳修改過的文件即可。