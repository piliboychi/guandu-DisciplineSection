[README.md](https://github.com/user-attachments/files/31946553/README.md)
# 關渡國小學務處生教組 — 公告網站使用說明

「一個總頁面 ＋ 各公告分頁」的家長公告網站。家長只會拿到**一個網址**（總頁面），點卡片即可進入各公告詳情。

## 一、檔案架構

| 檔案 | 用途 |
|---|---|
| `index.html` | **總頁面**：公告列表，家長進入的第一頁 |
| `uniform.html` | 115學年度制服購買公告（販售日程、夏/冬制服價格、平日補購、FAQ） |
| `uniform-rule.html` | 服裝規定：全校每週二穿著制服 |
| `forms.html` | 常用表單下載（請假單、臨時外出單、手機暨行動載具同意書） |
| `traffic.html` | 上放學交通與接送宣導（**範例頁**，內容請依學校實際狀況調整） |
| `template.html` | **新增公告用範本**（對外發布時不需上傳這個檔） |
| `README.md` | 本說明 |

> 學校名稱、生教組電話（02-2891-2847 轉 824）、地址等已全部設定為關渡國小真實資料。
> ⚠️ 發布前請搜尋「範例」二字，確認 `traffic.html` 的作息時間、警衛室分機等內容是否需修改。

## 二、各分頁內容與注意事項

- **uniform.html**：115學年度制服購買公告（**已改版**：取消 8/22、9/3 大門口現場販售，全面改為電話向一富有限公司訂購 → 轉帳付款 → 配送到校 → 學生帶回；價格為夏季 $300/$210（一套 $510）、冬季 $340/$300（一套 $640、10/30 前交貨）；一富專線 (02)2971-2213）。
  ⚠️ 若冬季制服實際仍走「三聯單收費」而非轉帳付款，請修改第二節冬季表格之「說明」欄。
- **forms.html**：表單下載按鈕直接連到**原網站 assets 的 Word（.doc）／PDF 檔**（`piliboychi.github.io/guandu-uniform/assets/…`），所以**請保留舊網站、不要刪除 assets 資料夾**，家長才能正常下載。（注意：原網站的「WORD 檔」按鈕其實是壞的——檔案為 .doc 而非 .docx，本版已修正。）
- **traffic.html**：為新寫的範例公告，時間、接送區位置、警衛室分機 199 為帶入的參考值，請改成學校實際資料；不需要此頁時，刪除該檔並移除 `index.html` 中對應卡片即可。

## 三、如何新增一則公告（4 步驟）

1. **複製** `template.html`，重新命名為公告名稱，例如 `uniform.html`、`uniform-rule.html`、`campus-safety.html`……（建議用英文檔名，避免 GitHub Pages 中文檔名出問題）。
2. 打開新檔案，修改：頁面標題（`<title>`）、大標題（`<h1>`）、日期、對象，以及正文內容。用不到的區塊（小節）直接刪掉；要表格或提示框就複製範例區塊。
3. 打開 `index.html`，在「公告清單」區複製一塊 `<a class="card">…</a>`，把連結改成新檔案名稱，修改分類標籤、標題、摘要、日期。
4. 上傳到 GitHub（見下節）。

**公告分類標籤顏色**（`index.html` 卡片上的 `<span class="tag …">`）：

| class | 顏色 | 適用 |
|---|---|---|
| `tag-toy` | 綠 | 制服、服裝 |
| `tag-life` | 紫 | 服儀規定、生活常規、獎懲 |
| `tag-form` | 藍 | 常用表單下載 |
| `tag-traffic` | 橘 | 交通安全、接送 |

## 四、如何發布到 GitHub Pages（沿用同一個網址）

**做法 A：用 GitHub 網頁直接上傳（免安裝軟體，推薦）**

1. 開啟 <https://github.com/piliboychi/guandu-uniform>。
2. 點畫面上方「**Add file**」→「**Upload files**」。
3. 把本資料夾裡的 `.html` 檔案（`index.html`、`uniform.html`、`uniform-rule.html`、`forms.html`、`traffic.html`，`template.html` 可不傳）**全部一起拖曳**到上傳區。
   - 同名檔案（`index.html`）會自動**覆蓋**舊版，畫面會顯示已取代，沒問題。
   - **不要把檔案放進子資料夾**，要直接放在上傳區（專案根目錄），分頁網址才會是 `…/guandu-uniform/uniform.html`。
   - ⚠️ **不要刪除 `assets` 資料夾**，表單下載連結才不會失效。
4. 下方 Commit 訊息可留預設，點「**Commit changes**」→ 選「**Commit directly to the main branch**」→「Commit changes」。
5. 等 1～2 分鐘，開啟 <https://piliboychi.github.io/guandu-uniform/> 看到「生教組公告專區」總頁面即成功；如還是舊畫面，按 **Ctrl+F5** 強制重新整理。

**做法 B：用 git 指令上傳（要裝 Git）**

```bash
git clone https://github.com/piliboychi/guandu-uniform.git
cd guandu-uniform
# 把新的 .html 檔複製進來（覆蓋舊 index.html）
git add .
git commit -m "更新：生教組公告專區多頁版"
git push origin main
```

**做法 C：另建新專案（網址會變）**：新建 repo → Settings → Pages → Source 選 `main` 分支，網址為 <https://piliboychi.github.io/新專案名/>，需重新分享給家長。

**打不開或畫面怪怪的檢查順序**：
① 是不是只上傳了總頁面、其他分頁檔沒上傳？→ 全部 .html 都要上傳
② 分頁有沒有被放進子資料夾？→ 必須在根目錄
③ 頁面舊快取？→ Ctrl+F5 強制重新整理
④ Settings → Pages 是否顯示「Your site is live at …」

## 五、發布前檢查清單

- [ ] `traffic.html` 中標示「範例」之處已改為學校實際資料（作息時間、接送區、警衛室分機等）
- [ ] `forms.html` 表單下載按鈕可正常開啟（舊網站 assets 仍存在）
- [ ] 用手機開啟 `index.html` 確認版面正常（家長大多用手機看）
- [ ] 點進每則公告，確認「← 回首頁」可正常跳回 `index.html`
- [ ] 每則公告的日期、對象已更新為正確資訊

## 六、常見修改

- **改顏色**：每個檔案 `<style>` 開頭的 `#14523e`（深綠）、`#1f7a5c`（中綠）、`#d97706`（橘）是主色，直接替換即可。
- **加圖片**：把圖片和網頁放同一資料夾，於內文中插入 `<img src="圖片檔名.jpg" style="max-width:100%;border-radius:10px">`。
- **公告過期**：刪除 `index.html` 中該張卡片即可（家長就看不到入口）；分頁檔可保留或一併刪除。
- **置頂公告**：在想要置頂的卡片內加 `<span class="pin">置頂</span>`，並把該卡片移到 `grid` 區塊最上面。
