# 譯聲 Live 0.7.24｜Windows x64 乾淨分享版

完整離線辨識／翻譯模型已隨附。作者：Keith Tseng。


## 7-Zip 官方下載與解壓圖解

**7-Zip 官方下載網址：[https://www.7-zip.org/download.html](https://www.7-zip.org/download.html)**  
請選擇 **Windows x64 的 .exe 安裝程式**。

**[下載完整操作說明（PDF）](https://github.com/Keith-Tseng/YiSheng-Live/releases/download/v0.7.24/USER_GUIDE.zh-TW.pdf)**

下載 `.001`、`.002`、`.003` 三個檔案並放在同一資料夾。**只需對 `.001` 按右鍵 → 7-Zip → 解壓縮**，其餘兩卷會自動一起讀取，不用各別解壓。Windows 11 若沒看到 7-Zip，請先點「顯示其他選項」。

![三個分卷放同一資料夾，從 .001 一次解壓完整程式](https://raw.githubusercontent.com/Keith-Tseng/YiSheng-Live/main/docs/extract-guide.png)


## 下載與啟動

1. 展開本頁 **Assets**，下載 **全部 `.7z.001`、`.002` 等分卷**及 `SHA256SUMS.txt`。
2. 將全部分卷放在同一資料夾，以 [7-Zip](https://www.7-zip.org/) 開啟 `.7z.001` 並解壓縮。
3. 開啟解壓後 `譯聲 Live 0.7.24` 資料夾中的 `譯聲 Live.exe`，保留所有附帶檔案。
4. 首次啟動等待模型準備完成；選擇語言和音訊來源，再按「開始聆聽」。

**不要下載 GitHub 自動提供的 Source code ZIP／tar.gz 當程式；裡面只有儲存庫文件。**

| 分卷 | 大小 |
|---|---:|
| [YiSheng-Live-0.7.24-Windows-x64.7z.001](https://github.com/Keith-Tseng/YiSheng-Live/releases/download/v0.7.24/YiSheng-Live-0.7.24-Windows-x64.7z.001) | 1.76 GiB |
| [YiSheng-Live-0.7.24-Windows-x64.7z.002](https://github.com/Keith-Tseng/YiSheng-Live/releases/download/v0.7.24/YiSheng-Live-0.7.24-Windows-x64.7z.002) | 1.76 GiB |
| [YiSheng-Live-0.7.24-Windows-x64.7z.003](https://github.com/Keith-Tseng/YiSheng-Live/releases/download/v0.7.24/YiSheng-Live-0.7.24-Windows-x64.7z.003) | 0.96 GiB |

[下載 SHA256SUMS.txt](https://github.com/Keith-Tseng/YiSheng-Live/releases/download/v0.7.24/SHA256SUMS.txt) · [下載完整操作說明（PDF）](https://github.com/Keith-Tseng/YiSheng-Live/releases/download/v0.7.24/USER_GUIDE.zh-TW.pdf)


## 版本重點

- 已包含停止聆聽後語言選單未解鎖的修正。切換語言前仍需先停止並等待處理、存檔完成。
- 中英自動／中文使用支援多語的 Whisper small；英文專用 Distil 不用來辨識中文。
- 分享版使用 `%APPDATA%\YiShengLive-Share`，首次開啟不匯入原版設定與紀錄；之後正常保存你在分享版建立的資料。
- 發布包不含製作者的金鑰、私人設定、對話、錄音或測試資料。完整保留第三方授權文件。

## 使用前須知

適用 Windows x64，建議預留 20 GB 空間。推論速度依硬體與模型而異；未提供全部硬體環境的效能保證。此版本未提供程式碼簽章；請確認下載來源及校驗碼，不必關閉系統防護。

本機模式不需要 API 金鑰。選用 Azure 語音時需自行設定，音訊會送到 Azure。辨識與翻譯仍可能出錯，重要內容請人工核對。

完整操作、校驗步驟及常見問題：[閱讀使用說明](https://github.com/Keith-Tseng/YiSheng-Live#readme)。
