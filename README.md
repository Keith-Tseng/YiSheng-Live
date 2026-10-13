# 譯聲 Live｜Windows 離線中英語音翻譯

譯聲 Live 是 Windows x64 桌面工具，提供麥克風／電腦音訊辨識、中英雙向翻譯、雙語逐句字幕、透明字幕、快速文字翻譯與本機對話紀錄。

**作者：Keith Tseng**  
[LinkedIn](https://www.linkedin.com/in/keith-tseng0721)

**目前發布：0.7.24 乾淨分享版。**這個儲存庫提供執行版下載與使用說明，並未發布本專案完整原始碼。

## 系統與空間準備

- 本包是 **Windows x64** 執行版；不是 macOS、Linux 或 Windows ARM 原生版本。
- 程式、離線模型與必要推論執行環境已隨附，不需要另外安裝 Python 或自行下載模型。
- 建議至少預留 **20 GB 可用磁碟空間**，容納全部下載分卷、解壓後程式與使用資料。
- 模型需要記憶體和運算時間。可用時會使用相容 GPU，否則走 CPU；速度因硬體、句長、模型及其他程式負載而異。尚未提供涵蓋各種硬體的效能保證。
- 解壓縮請使用 [7-Zip 官方版本](https://www.7-zip.org/)。不需要用管理員權限執行譯聲 Live。

## 第一次即時翻譯

1. 開啟「設定」，確認使用**本機離線模型**。預設不需要 API 金鑰。
2. 回到「即時翻譯」，選擇接收語言：英文、中文或中英自動。
3. 選擇音訊來源：**麥克風**用於現場說話；**電腦音訊**用於電腦正在播放的聲音。
4. 按「開始聆聽」。若系統詢問麥克風權限，依需求允許。
5. 以自然語速說完整句子，句尾稍作停頓，等待原文與譯文顯示。
6. 結束時按「停止聆聽」，等待最後片段處理與存檔完成。

**要切換語言、模型或音訊來源時，先停止聆聽並等待處理完成。**0.7.22 起修正了停止後語言選單未重新解鎖的問題，0.7.24 已包含此修正。

## 英文、中文與雙語模式

| 情境 | 選擇方式 | 注意事項 |
|---|---|---|
| 英文語音翻成繁體中文 | 單一英文 | 可使用 Distil-Whisper 英文模型 |
| 中文語音翻成英文 | 單一中文 | 使用支援多語的 Whisper small |
| 中英文輪流說話 | 中英自動 | 從主畫面切換時，若原先是英文專用模型，會改用已安裝的多語模型 |

Distil-Whisper Large v3.5 是英文專用選項，不適合中文辨識。中英自動會判斷片段語言；同一句快速混用兩種語言、多人重疊或非常短的聲音仍可能判斷不準。

## 模型選擇

| 元件 | 隨附選項 | 用途與限制 |
|---|---|---|
| 語音辨識 | Distil-Whisper Large v3.5 | 英文整句辨識；通常在完整句後顯示結果 |
| 語音辨識 | faster-whisper small | 支援中文、英文及中英自動；暫定字幕能力依設定與硬體而異 |
| 文字翻譯 | HY-MT2 1.8B Q4_K_M | 本機中英翻譯；GPU／CPU 路徑依可用環境選擇 |
| 文字翻譯 | Marian OPUS-MT INT8 | 可切換的本機翻譯選項 |

更換模型後按「儲存設定」，等待模型準備完成再開始聆聽。辨識與翻譯品質會受到口音、收音、句子上下文及模型能力影響，不能保證每句正確。

## 收音與字幕

- **麥克風**：先距離約 15–30 公分試說，再移到實際使用位置；實際距離依設備、環境與音量決定。
- **收音敏感度**：設定中往左更敏銳、往右較不敏銳。漏收輕聲可往左試調；雜音常觸發可往右調。拉霸不對應固定公尺數，儲存後下次聆聽生效。
- **電腦音訊**：先確認電腦有實際播放聲音。戴耳機可減少喇叭聲再被麥克風收進去。
- **完整句與暫定字幕**：不同模型的出字時機不同；沒有立即出字不一定代表沒有收音。
- **透明字幕**：可切換浮動顯示、調整字幕字級、拖曳及使用滑鼠穿透。功能列可收合；返回按鈕可回主畫面。
- **展開對話與縮放**：方便查看較多內容；介面提供 50%～150% 的對話版面縮放。
- **說話者標籤**：A、B 等是本場次的聲音分組，不是真實身分辨識；未知可能顯示 `?`，可手動修正。

## 快速文字翻譯與專業術語

- 「快速翻譯」可輸入或貼上文字，檢視與複製譯文。
- Windows 朗讀使用系統已安裝的語音；若無中文或英文語音，需要先在 Windows 安裝對應語音。
- 單字可能有多種意思；縮寫、品牌和型號也可能保留英文。遇到不明確譯文，補充完整句子通常更有幫助。
- 「設定 → 會議專業術語」可選擇內建產業分類，或加入自訂詞。儲存後下次開始聆聽生效，術語提示不保證每次辨識正確。

## 對話紀錄、資料位置與隱私


- 分享版資料目錄：`%APPDATA%\YiShengLive-Share`。可以貼到 Windows 檔案總管位址列開啟。
- 首次使用分享版不會自動匯入原版程式的紀錄；原版資料不會被刪除或搬動。
- 分享版之後會保存你自己建立的設定與紀錄。**「乾淨分享版」不是每次啟動都清空資料**；同一 Windows 帳號下不同分享版也會沿用此目錄。
- 對話可在紀錄頁搜尋、複製、匯出 Word／TXT 或刪除。使用清除功能前請先備份需要保留的資料。
- 在本機離線模式中，辨識與翻譯在電腦上執行，不需要把音訊或文字送到翻譯 API。
- 選用 **Azure Speech** 時，音訊會送至 Azure，需要你自行設定金鑰、區域與服務額度。這不是完全離線模式。
- 點擊 LinkedIn 或其他外部連結會開啟瀏覽器並連線至該網站。
- 如要轉交程式給其他人，請使用原始發布分卷，不要把自己的 AppData 資料夾一起打包。

## 常見問題

| 問題 | 處理方式 |
|---|---|
| `.001` 無法解壓、顯示資料錯誤 | 確認所有分卷都下載完成、名稱一致、放在同一資料夾；比對 SHA-256 並用 7-Zip 測試 |
| 下載的 ZIP 只有文件 | 下載到了 GitHub 自動生成的 Source code；請改下載 Assets 的 `.7z.001` 等全部分卷 |
| EXE 找不到模型或 DLL | 完整解壓所有檔案，保留整個目錄結構；不要單獨搬移 EXE |
| 無法切換中英自動 | 先停止聆聽並等最後片段與存檔完成；確認使用新版 EXE。若提示模型缺少，重新完整解壓 |
| 中文辨識不正確 | 切換到中文或中英自動，確認使用 Whisper small，而非英文專用 Distil |
| 開啟後看到之前的紀錄 | 先確認不是舊捷徑；分享版會保留你之前在分享版建立的紀錄，可在紀錄頁管理 |
| 沒有辨識結果 | 檢查 Windows 麥克風權限、輸入設備、音源選擇、音量與敏感度；極弱訊號可能被略過 |
| 翻譯比較慢 | 等待首次模型載入完成，關閉其他高負載程式；CPU、模型大小、長句及補救重試都會影響延遲 |
| A／B 分人不準 | 減少重疊說話與回音，讓每人說完整句子；必要時手動修正標籤 |
| 沒有朗讀聲音 | 確認音量與輸出設備，以及 Windows 是否已安裝對應語言語音 |
| Windows 顯示安全警示 | 確認此儲存庫、版本與校驗碼；不要為了執行而關閉系統安全防護 |

## 已知限制與問題回報

此版本已針對封裝完整性、作者連結、首次空白紀錄、語言模式切換及停止後解鎖做過檢查；不代表已涵蓋所有電腦、聲音環境與口音。

翻譯可能漏字或誤解專有名詞、數字、否定及條件句。重要用途請人工核對。低音量、多人同時說話及噪音仍可能影響辨識與分人。

回報問題請使用 [Issues](https://github.com/Keith-Tseng/YiSheng-Live/issues)，提供版本、Windows 版本、模型、音訊來源、操作步驟、預期與實際結果，以及已去識別化的錯誤訊息。**不要上傳 API 金鑰、私人對話或未經同意的錄音。**

## 版本與授權文件

- 本儲存庫發布執行版與操作文件，未另行授予本專案完整原始碼的開源授權。第三方程式、模型及執行環境仍依各自隨附條款使用。

## English quick start

Download **all** `YiSheng-Live-0.7.24-Windows-x64.7z.*` release assets into one folder. Open `.7z.001` with 7-Zip and extract the complete application. Run `譯聲 Live.exe` on Windows x64. Do not use GitHub's automatic **Source code** archives as the application download.

Local mode performs speech recognition and translation on your computer. Chinese and bilingual modes use the multilingual Whisper small model. Stop listening and wait for processing to finish before switching languages. The share edition stores its own data in `%APPDATA%\YiShengLive-Share`; it does not automatically import the original edition's history. Optional Azure mode sends audio to Azure.

## 下載程式

前往 **[v0.7.24 Releases 下載頁](https://github.com/Keith-Tseng/YiSheng-Live/releases/tag/v0.7.24)**，展開 **Assets**，下載該版本的**全部分卷**。每卷小於 GitHub 的 2 GiB 限制。

| 分卷 | 大小 |
|---|---:|
| [YiSheng-Live-0.7.24-Windows-x64.7z.001](https://github.com/Keith-Tseng/YiSheng-Live/releases/download/v0.7.24/YiSheng-Live-0.7.24-Windows-x64.7z.001) | 1.76 GiB |
| [YiSheng-Live-0.7.24-Windows-x64.7z.002](https://github.com/Keith-Tseng/YiSheng-Live/releases/download/v0.7.24/YiSheng-Live-0.7.24-Windows-x64.7z.002) | 1.76 GiB |
| [YiSheng-Live-0.7.24-Windows-x64.7z.003](https://github.com/Keith-Tseng/YiSheng-Live/releases/download/v0.7.24/YiSheng-Live-0.7.24-Windows-x64.7z.003) | 0.96 GiB |

[下載 SHA256SUMS.txt](https://github.com/Keith-Tseng/YiSheng-Live/releases/download/v0.7.24/SHA256SUMS.txt)


> 不要使用綠色 Code 按鈕的 Download ZIP，也不要下載 Releases 自動附上的 Source code (zip/tar.gz) 當成程式。那些只包含此儲存庫的文件，沒有執行檔或模型。

## 分卷解壓縮：第一次使用請照這裡做

1. 下載 Assets 裡全部 `YiSheng-Live-0.7.24-Windows-x64.7z.001`、`.002` 等檔案。
2. 把它們放在**同一個資料夾**。不要更改檔名，不要混用不同版本的分卷。下載完成前不要開始解壓。
3. 用 7-Zip 開啟 **`.7z.001` 第一卷**，選擇「解壓縮」，解壓至一般可寫入資料夾，例如 `D:\Apps\YiSheng-Live`。
4. 7-Zip 會自動讀取其餘分卷；**不要分別解壓每一卷**。分卷本身不能獨立使用。
5. 進入解壓後的 `譯聲 Live 0.7.24` 資料夾，雙擊 **`譯聲 Live.exe`**。
6. 保留整個資料夾，包括 `resources`、`locales`、DLL 與授權文件。不要只搬移 EXE，也不要在壓縮檔裡直接執行。
7. 初次啟動需載入／預熱模型，請等待狀態完成。若要桌面捷徑，請對這次解壓的 EXE 建立捷徑，避免開到舊版本。

程式目前未提供程式碼簽章，Windows 可能顯示信任提示。遇到警示時請先確認下載來源與校驗碼；不需要關閉防毒或系統保護功能。

## 驗證下載是否完整

同時下載 `SHA256SUMS.txt`，在分卷所在資料夾開啟 PowerShell：

```powershell
Get-FileHash .\YiSheng-Live-0.7.24-Windows-x64.7z.* -Algorithm SHA256 |
  Select-Object Hash, Path
```

逐一對照檔名與 SHA-256（英文大小寫不影響比對）。若不一致，重新下載該卷。也可以在 7-Zip 對第一卷執行「測試」；缺卷、損毀或尚未下載完畢時不要繼續使用。

## 7-Zip 官方下載與解壓圖解

**7-Zip 官方下載網址：[https://www.7-zip.org/download.html](https://www.7-zip.org/download.html)**  
請選擇 **Windows x64 的 .exe 安裝程式**。

下載 `.001`、`.002`、`.003` 三個檔案並放在同一資料夾。**只需對 `.001` 按右鍵 → 7-Zip → 解壓縮**，其餘兩卷會自動一起讀取，不用各別解壓。Windows 11 若沒看到 7-Zip，請先點「顯示其他選項」。

![三個分卷放同一資料夾，從 .001 一次解壓完整程式](https://raw.githubusercontent.com/Keith-Tseng/YiSheng-Live/main/docs/extract-guide.png)

**[下載完整操作說明（PDF）](https://github.com/Keith-Tseng/YiSheng-Live/releases/download/v0.7.24/USER_GUIDE.zh-TW.pdf)**
