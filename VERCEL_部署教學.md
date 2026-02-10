# 使用 Vercel 部署「Chen Dig Quickly」網頁

**專案位置：** `桌面 / Bauhyphen_App / Search_ChenDigQuickly`  
（完整路徑：`/Users/apple/Desktop/Bauhyphen_App/Search_ChenDigQuickly`）

之後此專案相關檔案都放在此資料夾。

---

照著下面步驟做，就能把網頁放到網路上，讓別人用網址開啟。

---

## 事前準備

1. **安裝 Node.js**（若還沒裝）
   - 到 https://nodejs.org/ 下載並安裝（選 LTS 版本）。
   - 裝好後打開「終端機」，輸入：
     ```bash
     node -v
     ```
     有出現版本號（例如 `v20.x.x`）就代表成功。

2. **註冊 Vercel 帳號**
   - 打開 https://vercel.com
   - 點「Sign Up」，用 **GitHub** 或 **Email** 註冊（建議用 GitHub，之後要改版比較方便）。

---

## 方法一：用 Vercel 網頁 + GitHub（推薦，之後改版方便）

### 步驟 1：把專案放到 GitHub

1. 到 https://github.com 登入，點右上角 **+** → **New repository**。
2. Repository name 隨便取（例如：`chen-dig-quickly`），選 **Public**，然後 **Create repository**。
3. 在電腦上打開「終端機」，切到專案資料夾：
   ```bash
   cd /Users/apple/Desktop/Bauhyphen_App/Search_ChenDigQuickly
   ```
4. 若還沒用過 Git，先設定（只做一次）：
   ```bash
   git config --global user.name "你的名字"
   git config --global user.email "你的email@example.com"
   ```
5. 在專案資料夾裡執行：
   ```bash
   git init
   git add search.html vercel.json
   git commit -m "第一次上傳：搜尋比價網頁"
   git branch -M main
   git remote add origin https://github.com/你的帳號/chen-dig-quickly.git
   git push -u origin main
   ```
   （把 `你的帳號/chen-dig-quickly` 換成你剛建的 repository 網址）

### 步驟 2：用 Vercel 連到 GitHub 並部署

1. 打開 https://vercel.com 並登入。
2. 點 **Add New…** → **Project**。
3. 選 **Import Git Repository**，找到你剛 push 的 repository（例如 `chen-dig-quickly`），點 **Import**。
4. **Project Name** 可改可不改（會變成網址的一部分）。
5. **Root Directory** 維持預設（不要改）。
6. 直接點 **Deploy**，等約 1 分鐘。
7. 完成後會出現 **Visit**，點進去就是你的網址，例如：
   - `https://chen-dig-quickly-xxx.vercel.app`

之後只要在專案資料夾改好 `search.html`，再執行：

```bash
cd /Users/apple/Desktop/Bauhyphen_App/Search_ChenDigQuickly
git add search.html
git commit -m "更新網頁"
git push
```

Vercel 會自動重新部署，別人看到的就會是最新版本。

---

## 方法二：用 Vercel 指令（不碰 GitHub，最快）

適合「只想先放上去、暫時不用 Git」的情況。

### 步驟 1：安裝 Vercel CLI

在終端機執行（只需做一次）：

```bash
npm install -g vercel
```

若出現權限錯誤，可改用：

```bash
sudo npm install -g vercel
```

### 步驟 2：登入 Vercel

```bash
vercel login
```

終端機會給你一個網址，用瀏覽器打開並登入／註冊 Vercel，完成後回到終端機即可。

### 步驟 3：在專案資料夾裡部署

1. 切到專案資料夾：
   ```bash
   cd /Users/apple/Desktop/Bauhyphen_App/Search_ChenDigQuickly
   ```

2. 第一次部署：
   ```bash
   vercel
   ```

3. 照提示回答（通常直接按 Enter 即可）：
   - **Set up and deploy?** → 選 **Y**
   - **Which scope?** → 選你的帳號（Enter）
   - **Link to existing project?** → 選 **N**
   - **Project name?** → 直接 Enter（或用自己想要的英文名，例如 `chen-dig-quickly`）
   - **In which directory is your code?** → 輸入 **./** 再 Enter

4. 跑完後終端機會給一個網址，例如：
   - `https://search-chendigquickly-xxx.vercel.app`
   - 或 `https://chen-dig-quickly-xxx.vercel.app`

這個網址就是你的網頁，根目錄 `/` 會自動打開 `search.html`（因為專案裡有 `vercel.json` 設定）。

---

## 之後要更新網頁（方法二）

在專案資料夾執行：

```bash
cd /Users/apple/Desktop/Bauhyphen_App/Search_ChenDigQuickly
vercel --prod
```

`--prod` 會更新正式網址的內容；第一次用 `vercel` 時若已經連結過專案，之後都會更新同一個網址。

---

## 常見問題

**Q：網址可以自訂嗎？**  
A：可以。在 Vercel 後台 **Project → Settings → Domains** 裡可加自己的網域，或使用 Vercel 提供的 `xxx.vercel.app` 子網域。

**Q：只有 search.html，需要特別設定嗎？**  
A：不用。專案裡已加上 `vercel.json`，訪客打開根網址就會看到搜尋頁。

**Q：部署後別人開連結被擋（彈出視窗／分頁）？**  
A：那是瀏覽器阻擋多個新分頁，請對方在網址列旁允許此網站的彈出視窗即可。

---

完成後，把 Vercel 給你的網址傳給別人，對方就能在瀏覽器打開你的「Chen Dig Quickly」搜尋頁。
