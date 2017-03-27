---
title: "建立 Visual Studio 2017 的離線安裝程式 | Microsoft Docs"
description: "了解如何建立 Visual Studio 的離線安裝程式。"
ms.custom: 
ms.date: 03/07/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- offline installer [Visual Studio]
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
ms.sourcegitcommit: 91fde66abf2f325ef0a6a0a2fd30e36981f44033
ms.openlocfilehash: acb47946c29d99cb53b34d67fe8a26f5611307f9
ms.lasthandoff: 03/08/2017

---
# <a name="create-an-offline-installer-for-visual-studio-2017"></a>建立 Visual Studio 2017 的離線安裝程式
我們了解許多客戶都想要 [Visual Studio 2017](https://go.microsoft.com/fwlink/?linkid=844067) 的離線安裝程式。 雖然我們並未提供 ISO 映像，但建立一個可供您在離線時用來安裝的資料夾相當簡單。

方式如下：

## <a name="download-the-setup-file-you-want"></a>下載您想要的安裝檔
**[下載](https://www.visualstudio.com/downloads?utm_source=mscom&utm_campaign=msdocs)**您想要的 Visual Studio 版本。 請務必按一下 [儲存]，然後按一下 [開啟資料夾]。

您的安裝檔 &mdash; 或更具體來說，一個啟動載入器檔案 &mdash; 將與下列其中一個相符。

|版本 | 檔案|  
|-------------|-----------------------|  
|Visual Studio 企業版 |**vs_enterprise.exe**|  
|Visual Studio Professional |**vs_professional.exe**|  
|Visual Studio 社群 |**vs_community.exe**|

## <a name="create-an-offline-installation-folder"></a>建立離線安裝資料夾
若要建立包含所有語言和所有功能的離線安裝，請下列範例中的其中一個命令。

(請確定您是從 [下載] 目錄執行命令。 通常在執行 Windows 10 的電腦上，這會是 `C:\Users\<username>\Downloads`)。

- 針對 Visual Studio Enterprise，請執行： <br>  ```vs_enterprise.exe --layout c:\vs2017offline```
- 針對 Visual Studio Professional，請執行： <br> ```vs_professional.exe --layout c:\vs2017offline```
- 針對 Visual Studio Community，請執行： <br> ```vs_community.exe --layout c:\vs2017offline```

如需更多範例，請參閱此頁面上的[如何自訂您的離線安裝程式](#how-to-customize-your-offline- installer)一節。

## <a name="install-from-the-offline-installation-folder"></a>從離線安裝資料夾安裝
請現在或稍後執行離線安裝；您可以自行決定。 但當您要執行此操作時，請依照下列步驟執行。

  1. 安裝憑證 (它們會在 [配置] 資料夾的 [憑證] 資料夾中。 直接按一下每個憑證來安裝它)。

  2. 執行安裝檔案。 例如，執行： <br> ```c:\vs2017offline\vs_enterprise.exe```

## <a name="additional-tips-for-offline-installers"></a>其他離線安裝程式秘訣
自訂或更新您的離線安裝程式相當簡單，我們將示範如何執行這項操作。 如果您的離線安裝程式發生問題，我們也會提供您疑難排解和支援資訊。

### <a name="how-to-customize-your-offline-installer"></a>如何自訂您的離線安裝程式
有許多選項可供您用來自訂離線安裝程式。 以下是一些如何透過[語言地區設定](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)自訂它的範例。

 - 若要下載僅適用於一種語言的所有工作負載和元件，請執行： <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - 若要下載適用於多種語言的所有工作負載和元件，請執行： <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - 若要下載適用於所有語言的一個工作負載，請執行： <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure ```
 - 若要下載適用於三種語言的兩個工作負載和一個選擇性元件，請執行： <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure Microsoft.VisualStudio.Workload.ManagedDesktop Component.GitHub.VisualStudio --lang en-US de-DE ja-JP ``` 若要深入了解您可用來自訂安裝的選項，請參閱[使用命令列參數安裝 Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md) 頁面。


### <a name="how-to-update-an-offline-installer"></a>如何更新離線安裝程式
您可以在稍後的日期再更新您的離線安裝程式。 方式如下：
* 若要更新您從離線安裝資料夾安裝的 Visual Studio 執行個體，請執行「Visual Studio 安裝程式」，然後按一下 [更新]。
* 若要重新整理您的離線安裝資料夾，以便讓它包含最新的更新，請再次執行 ```--layout``` 命令。 請務必指向您之前使用的相同資料夾；如此一來，才會只下載自您上次執行 ```--layout``` 之後已更新的元件。


如果您想要更新離線安裝，請再次執行 `--layout` 命令。 請務必指向您之前使用的相同資料夾；如此一來，才會只下載自您上次執行 `--layout` 之後已更新的元件。

### <a name="how-to-troubleshoot-an-offline-installer"></a>如何針對離線安裝程式進行疑難排解
有時會發生一些問題。 下表是已知的問題及一些可能有幫助的因應措施。

| 問題       | 項目                   | 方案 |
| ----------- | ---------------------- | -------- |
| 您收到有關無法安裝某些元件和套件的警告訊息。  | Android SDK 安裝程式 (API 層級) | 如果您想要包含 Android SDK (API 層級) 套件，則在您建立離線安裝程式時，必須有網際網路連線。 如果您是在受限制的網路上，則必須允許存取下列 URL： <br><br> - http://dl.google.com:443 <br> - http://dl-ssl.google.com:443 <br>  - https://dl-ssl.google.com/android/repository/*<br><br>如需如何解決可能 Proxy 設定問題的詳細資訊，請參閱 [Visual Studio install failures (Android SDK Setup) behind a Proxy](https://blogs.msdn.microsoft.com/peterhauge/2016/09/22/visual-studio-2015-install-failures-android-sdk-setup-behind-a-proxy/) (受 Proxy 保護的 Visual Studio 安裝失敗 (Android SDK 安裝程式)) 部落格文章。  |  
| 使用者沒有檔案的存取權。 | 權限 (ACL) | 請務必在您共用離線安裝「之前」調整權限 (ACL)，讓它們將「讀取權」授與其他使用者。 |
| 無法安裝新的工作負載、元件或語言。  | `--layout`  | 如果您要從某個部分配置安裝，請確定您能夠存取網際網路，然後選取先前配置中沒有的工作負載、元件或語言。 |

### <a name="how-to-get-support-for-your-offline-installer"></a>如何取得離線安裝程式的支援
如果您的離線安裝發生問題，我們會想要進行了解。 告訴我們的最簡單方式就是使用[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具。 使用此工具時，您可以將我們所需的遙測和記錄檔傳送給我們，來協助我們診斷及修正問題。

我們也提供其他支援選項。 如需這些支援的清單，請參閱[告訴我們](../ide/how-to-report-a-problem-with-visual-studio-2017.md)頁面。


## <a name="see-also"></a>請參閱
* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)

