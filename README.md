# chiiiiiitrip — 行程總覽 (簡易靜態 WebApp)

此專案包含三個旅遊方案的手機優先單頁 WebApp 範例，已放在 `plans/` 資料夾：

- `plans/index.html` — 三方案整合的手機優先 WebApp（日式極簡設計）
- `plans/zhangjiajie_deep_explore.html` — 原始方案一（張家界）
- `plans/changsha_wuhan_culture.html` — 原始方案二（長沙+武漢）
- `plans/jingdezhen_nanchang_art.html` — 原始方案三（景德鎮+南昌）

快速在本機檢視（在 devcontainer / Ubuntu 環境下）：

1. 開啟終端機，切換到專案根目錄（含 `plans/`）：

```bash
cd /workspaces/chiiiiiitrip
```

2. 使用 Python 內建的簡易 HTTP 伺服器（會在目前目錄提供靜態檔案）：

```bash
python3 -m http.server 8000
```

3. 在瀏覽器打開（host machine）：

- 若在 devcontainer 或遠端環境，請使用對應的 forwarded port；本機則開啟：

```
http://localhost:8000/plans/index.html
```

主要功能說明：

- 手機優先的 UI：大按鈕、圓角卡片、水平日期分頁、觸控友善。
- 三個主按鈕可切換三個行程方案，每個方案再以日期分頁切換每日卡片。
- 卡片支援 `data-highlights` 屬性，將自動產生「必吃 / 必點 / 必買」色彩標籤。
- 卡片內的導航按鈕會打開 Google Maps 的查詢（簡易示範）。

下一步建議（可由我協助）：

- 把每個卡片加入實際的示意圖片（將檔案置於 `plans/images/` 並更新 `src`）。
- 將 `data-highlights` 的內容由服務端或簡單的 JSON 檔維護，提供編輯介面。
- 加入雙語切換（中 / 英）或導出為 PDF 的列印樣式。

需要我立即替你：
- 把示意圖片加入並更新卡片 `src`？（請上傳圖片或告訴我 URL）
- 加入英文版或雙語切換？

如何在 iPhone (Safari) 加入「主畫面」並顯示自訂圖示

1. 我已在 `plans/` 中放一個示意 SVG：`plans/images/icon.svg`，以及 `manifest.json` 與 head 連結標籤。iOS Safari 會使用 apple-touch-icon (PNG) 作為主畫面圖示；請將你要的圖示轉成 PNG 並放到 `plans/images/` 下，檔名為：

	- `apple-touch-icon.png` (推薦 180x180)
	- 可選：`icon-192.png`、`icon-512.png`（對應 manifest 中的規格）

2. 在開發機或 devcontainer 裡可以用 ImageMagick 快速轉檔：

```bash
# 如果沒有 install，可先安裝（Ubuntu）
sudo apt update && sudo apt install -y imagemagick

# 由 svg 產生 180x180 的 PNG
convert plans/images/icon.svg -resize 180x180 plans/images/apple-touch-icon.png

# 生成 manifest 用的尺寸
convert plans/images/icon.svg -resize 192x192 plans/images/icon-192.png
convert plans/images/icon.svg -resize 512x512 plans/images/icon-512.png
```

3. 在 iPhone 上測試：
	- 使用 Safari 開啟 `http://<你的 host>:8000/plans/index.html`（或在 devcontainer 中使用 forwarded port）。
	- 點選下方分享按鈕 -> 選擇「加入主畫面 / Add to Home Screen」。
	- 設定名稱後確認，應會使用 `apple-touch-icon.png` 作為主畫面圖示（如果 iOS 快取舊圖示，請清除 Safari 快取或重新啟動裝置）。

如果你要我直接替你把 `plans/images/icon.svg` 轉成 PNG 並放好（我可以在此環境嘗試用 ImageMagick 轉檔），請回覆「請轉檔」，我會執行並回報結果。 

