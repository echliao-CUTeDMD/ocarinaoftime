# 春風陶笛 · Ocarina Studio

可離線使用的陶笛音樂播放器，支援預設歌曲、樂譜上傳、數字簡譜轉換與基礎圖片／PDF 讀譜。

## 開啟方式

直接以新版 Chrome 或 Edge 開啟 `index.html`，按「開始演奏」即可。音效須經使用者點擊後啟動。

本套件不需要 npm、建置程序、伺服器或 API 金鑰。JavaScript、樣式與 PDF.js 已內嵌於 `index.html`。上傳的樂譜只在瀏覽器內處理，不會傳送到外部服務。

## 上傳 GitHub 並啟用網站

1. 解壓縮套件，在 GitHub 建立一個 repository（例如 `ocarina-studio`）。
2. 選擇 **Add file → Upload files**，上傳解壓縮後的內容。請讓 `index.html` 直接位於 repository 最上層，不要只上傳 ZIP 或包在另一層資料夾內。
3. 提交檔案到 `main` 分支。
4. 前往 **Settings → Pages → Build and deployment**。
5. Source 選 **Deploy from a branch**，Branch 選 **main**，資料夾選 **/(root)**，按 **Save**。
6. 等待部署完成，在 Pages 頁面開啟 GitHub 顯示的網站網址。一般專案網址為 `https://你的帳號.github.io/ocarina-studio/`。

GitHub Free 可使用公開 repository 的 Pages。以 GitHub Pages 設定頁顯示的網址與部署狀態為準。

[GitHub Pages 官方設定說明](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

## 功能

- 陶笛合成音色、播放／暫停、停止、循環、速度與音量調整。
- 6 首預設歌曲：望春風、小星星、歡樂頌、搖籃曲、平安夜、給愛麗絲〈主題段〉。
- 播放時同步標示數字簡譜；可點擊音符試聽，或以 A S D F G H J K 演奏。
- 上傳 TXT 簡譜與未壓縮 MusicXML（`.xml`、`.musicxml`）。
- 依指定調性轉換數字簡譜，編輯並下載 TXT。
- 上傳 PNG、JPG、WebP、PDF，產生可校正的簡譜草稿。

## 簡譜格式

以空白分隔音符。1～7 是所選調性的音階，0 是休止符。逗號降低八度，單引號提高八度；冒號後為拍數，省略即為 1 拍。`#4`、`b7` 表示升降音，`|` 分隔小節。

```text
# 調性：1=C5
1 2 3:0.5 0:0.5 | 5:2 1':2 | 5, 1:3
```

## 讀譜範圍

MusicXML 讀取第一聲部、第一聲線，處理音高、拍長、休止符與延音線；和弦取主音符，不展開反覆或裝飾音，演奏速度依 BPM 滑桿設定。

圖片／PDF 辨識是基礎輔助草稿，適用清晰、水平、印刷、單旋律高音五線譜。自動定位五線與音符頭，實心暫設 1 拍，空心暫設 2 拍。節奏、附點、休止符、臨時升降記號、反覆等需人工校正，原譜調號由使用者設定。複雜多聲部、低音譜、手寫或模糊照片不支援可靠辨識。

PDF 每次處理一頁；可逐頁辨識，校正後接到目前樂曲後面。按圖上的標記可刪除誤判，點五線附近可補音。重新辨識、修改調號或點圖會重新產生草稿，請先保留文字修正內容。

## 檔案

- `index.html`：完整網站，也可直接離線開啟。
- `examples/`：MusicXML、文字簡譜、圖片與掃描 PDF 範例。
- `docs/`：操作說明與介面預覽。
- `THIRD_PARTY_NOTICES.md`、`licenses/`：第三方元件與曲目來源資訊。
- `.nojekyll`：靜態網站標記。

## 驗證

已檢查 6 首預設曲的簡譜解析、總拍數與音域，並操作驗證歌曲切換與播放。MusicXML 匯入已驗證音高、休止符及延音線；影像功能已使用合成 PNG 與掃描 PDF 驗證 8 個音符的定位及轉換，尚未以大量真實照片評估辨識準確率。

## 曲目與元件資訊

本播放器使用原曲的單旋律整理與 Web Audio 合成聲音，未包含商業錄音或歌詞。曲目作者與來源顯示在網頁底部，詳見 [第三方與曲目資訊](THIRD_PARTY_NOTICES.md)。
