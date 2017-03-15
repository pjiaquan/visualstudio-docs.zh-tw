---
title: "建立 Visual Studio 2017 RC 的離線安裝 | Microsoft Docs"
description: "了解如何建立 Visual Studio 的離線安裝。"
ms.custom: 
ms.date: 02/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- ISO [Visual Studio]
ms.assetid: 7bd7e724-7bfd-43f1-9935-981919be5a00
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: d4d1bd45ce697017480b3f63d0c7feb5ab20d2d6
ms.openlocfilehash: 33e765d205aa7ad8a3d8c5b871863ab659092a77
ms.lasthandoff: 02/22/2017

---
# <a name="create-an-offline-installation-of-visual-studio-2017-rc"></a>建立 Visual Studio 2017 RC 的離線安裝

## <a name="create-a-layout"></a>建立版面配置
如果您想要在另一部沒有網際網路存取的電腦上安裝 [Visual Studio 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/)，則作法是先建立包含所有需要之 Visual Studio 檔案和元件的離線安裝版面配置。

您接著可以使用所建立的離線安裝版面配置將 Visual Studio 安裝至目標電腦。     

> [!WARNING]
> Android SDK 目前尚不支援離線安裝體驗。 如果您將 Android SDK 安裝程式的項目安裝在未連線至網際網路的電腦，安裝可能會失敗。 如需此問題的詳細資訊，請移至本主題中的[針對離線安裝進行疑難排解](#tshootofflineinstall)小節。


#### <a name="to-create-an-offline-installation-layout-of-visual-studio"></a>建立 Visual Studio 的離線安裝版面配置
1. 將 Visual Studio 安裝程式可執行檔下載至您本機電腦上的磁碟機。
  例如，[下載 vs_enterprise.exe 檔案](https://www.visualstudio.com/vs/visual-studio-2017-rc/)。
2. 從命令提示字元中，執行具有下列引數 (參數) 的 `vs_enterprise.exe`︰

   a. 新增 `--layout <path>`，其中 `<path>` 是您想要將版面配置下載至其中的位置。 請注意，目前不支援相對路徑 (例如 `..\vs2017`)。 預設會下載所有語言 (請參閱範例 A)。

   b. 提供 `--lang <language>` 引數，以將下載限制為一部分的可用語言，其中 `<language>` 是一個或多個語言地區設定  (請參閱範例 B 和範例 C)。

   c.  提供 `--add <package ID>` 引數，以將下載限制成一小部分的工作負載和元件。 這只會下載您所指定的工作負載和元件 (及其相依性) (請參閱範例 D 和範例 E)。

   如需依 Visual Studio 產品排序之工作負載和元件識別碼的完整清單，請參閱 [Visual Studio 2017 Workload and Component IDs](https://aka.ms/vs2017componentids) (Visual Studio 2017 工作負載和元件識別碼) 頁面。

### <a name="examples"></a>範例
**範例 A**：下載所有語言的所有工作負載和元件
  > ```vs_enterprise.exe --layout C:\vs2017```

**範例 B**：下載某種語言的所有工作負載和元件  
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US```

**範例 C**：下載多種語言的所有工作負載和元件
  > ```vs_enterprise.exe --layout C:\vs2017 --lang en-US de-DE ja-JP```

**範例 D**：下載所有語言的一個工作負載
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure ```

**範例 E**：下載三種語言的兩個工作負載和一個選擇性元件
  > ```vs_enterprise.exe --layout C:\vs2017 --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ```

  > [!WARNING]
  > 如果 setup .exe 檔案名稱包含數字，--layout 參數將會失敗。 若要解決此問題，您必須將檔名的數字移除&mdash;例如，將 *vs_community__198521760.1486960229.exe* 重新命名為 ***vs_community.exe***。

### <a name="language-locales"></a>語言地區設定

| 語言地區設定 | 語言 |
| -----   | ----- |
| cs-CZ    | 捷克文 |
| de-DE    | 德文 |
| zh-TW    | 英文 |
| es-ES    | 西班牙文 |
| fr-FR    | 法文 |
| it-IT    | 義大利文 |
| ja-JP    | 日文 |
| ko-KR    | 韓文 |
| pl-PL    | 波蘭文 |
| pt-BR    | 葡萄牙文 - 巴西 |
| ru-RU    | 俄文 |
| tr-TR    | 土耳其文 |
| zh-CN    | 簡體中文 |
| zh-TW    | 繁體中文 |


## <a name="install-from-a-layout"></a>從版面配置安裝
#### <a name="to-install-visual-studio-from-an-offline-installation-layout"></a>從離線安裝版面配置安裝 Visual Studio
1. 在目標電腦上，巡覽至 [配置] 資料夾中的 [憑證] 資料夾。
2. 按一下滑鼠右鍵並安裝 [憑證] 資料夾中的每個憑證

  (如果系統在您安裝憑證之後提示您輸入密碼，請按一下 [繼續])。  
3. 從 [版面配置] 資料夾執行 `vs_enterprise.exe`。

注意︰如果您要從部分版面配置中安裝，並選取版面配置中沒有的工作負載、元件或語言，則安裝程式會嘗試下載它們。  如果您沒有網際網路存取，則無法安裝這些項目。

> [!CAUTION]
> 離線安裝配置目前會使用防止所有使用者存取的受限權限 (ACL) 來建立一些檔案。  請務必在您共用離線安裝*之前*調整權限 (ACL)，讓他們將讀取權授與其他使用者。

## <a name="update-an-installation-layout"></a>更新安裝版面配置
Visual Studio 2017 RC 具有可用更新時，您可以再次執行指向相同版面配置資料夾的 `--layout` 命令，確保資料夾包含最新元件。 只會下載已在上次執行 `--layout` 後更新的那些元件。

## <a id="tshootofflineinstall"> </a>針對安裝版面配置進行疑難排解
當您從離線安裝快取中離線安裝時，可能會看到無法安裝某些元件和套件的警告訊息。 下表包含這些情況下的可能方案。

| 元件或套件 | 方案 |
| -------------------- | -------- |
|Android SDK 安裝程式 (API 層級)| 您必須連接網際網路，才能安裝 Android SDK (API 層級) 套件。 如果您是在受限網路上，則必須在安裝 Visual Studio 時允許存取下列 URL： <br><br> - http://dl.google.com:443 <br>- http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>如需如何解決可能 Proxy 設定問題的詳細資訊，請參閱 [Visual Studio install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (受 Proxy 保護的 Visual Studio 安裝失敗 (Android SDK 安裝程式)) 部落格文章。  |  

 > [!IMPORTANT]
 > 雖然 Visual Studio 2017 RC 一般支援在生產環境中使用，但安裝 UI 中標示為「預覽」的這些工作負載和元件不支援在生產環境中使用。

 ## <a name="see-also"></a>請參閱
 * [安裝 Visual Studio](install-visual-studio.md)
 * [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [回報 Visual Studio 的問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

