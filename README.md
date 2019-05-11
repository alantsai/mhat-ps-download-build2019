# mhat-ps-download-build2019

([english summary](#English-Summary))

這個Powershell的script用來下載Microsoft 2019 Build大會的所有影片以及資源。

每一個下載下來的Session會包含(如果有提供的話):
1. 影片 (*.mp4)
2. 字幕 (*.vtt)
3. 説明文字 (*.txt)
4. slide (*.pptx)

原始碼由微軟官方提供：https://mybuild.techcommunity.microsoft.com/VideoDownloader/Download-BuildResources.zip

經過修改增加了幾個部分：
1. 下載的資料夾除了原本的Session Code還包含了Title
2. 下載的檔案包含了字幕
3. 説明文字(.txt)包含了最後更新日期 - 未來或許可以用這個欄位判斷是否需要更新内容

## 快速使用 (how to use)

只需要clone或者下載這個專案:
1. 開啓 powershell
2. `cd` 進入 `src` 資料夾
3. 執行：`.\Download-BuildResources.ps1 -directory .\Download` 將會下載所有已經公佈的session到當前目錄下的 `Download` 資料夾

> 如果Session内容已經下載過了，不會被重複下載

### 使用參數

總共有兩個可選參數：

- `-directory` - 決定要下載到那邊，預設是script的位置
- `-sessionCodes` - 要下載的session，用逗點分割。例如：`-sessionCodes "CFS3006,BRK2006"`。預設是空，表示下載**全部**session

### 注意事項

- 如果Session還沒有提供任何影片的鏈接，那麽會被直接忽略 - 不會建立任何資料夾
- Session影片會由微軟更新上去 - 因此還沒有提供的影片可能等幾天就會有了

### 使用範例

如果要下載全部的Session到當前的資料夾下面的Download

```powershell
.\Download-BuildResources.ps1 -directory .\Download
```

如果要下載指定的Session到當前的資料夾下面的Download

```powershell
.\Download-BuildResources.ps1 -directory .\Download -sessionCodes "CFS3006,BRK2006"
```

## English Summary

This Powershell script is used for downloading all available Microsoft 2019 Build videos and slides.

Each downloaded session will include (if available):
1. video (*.mp4)
2. caption (*.vtt)
3. description text (*.txt)
4. slide (*.pptx)

The original script are provided by Microsoft: 
https://mybuild.techcommunity.microsoft.com/VideoDownloader/Download-BuildResources.zip

Base on the original script It has been modified to include:
1. Downloaded session folder name originally only contain session code, now the folder name will also include title of the session.
2. Download will include the caption for the video
3. In the description text include `last update time` - can be used in future to know if video has been updated or not for an update download


## 原文件説明 (Original ReadMe from source code)

Powershell script for downloading all of the build 2019 videos and PowerPoint slide decks.

Videos will become available as they are published. Some sessions don't have videos or slide decks available

---Parameters---
-director: The directory into which the videos are to be downloaded. If this is not set it will default to the folder in which the script is located.
-sessionCodes:  A comma separated list of session codes which can be used to filter the download for only specific sessions. There is no limit as to the number that may be specified.

---Notes---
* If a session does not have a slide desk or a video, no folder or associated metadata file will be created. That session will just be skipped.
* Leaving the -sessionCodes parameter blank will cause the script to download all session videos/slide decks where they exist.

To run the script, open a PowerShell window to the directory in which the script is located.
To download every thing run the following
.\Download-BuildResources.ps1


To download every thing into a given directory run the following
.\Download-BuildResources.ps1 C:\Build2019

To download a set of sessions, supply the session code like this:
.\Download-BuildResources.ps1 -directory . -sessionCodes "KEY,TK01,TK02,BRK3016"


## 授權 (License)

本專案屬於 MIT License，更多資訊請看 [LICENSE.md](LICENSE.md)
