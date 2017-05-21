---
title: "建立 Visual Studio 的網路型安裝 | Microsoft Docs"
description: '{{PLACEHOLDER}}'
ms.date: 05/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 4CABFD20-962E-482C-8A76-E4012052F701
author: timsneath
ms.author: tims
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 85576806818a6ed289c2f660f87b5c419016c600
ms.openlocfilehash: c8c48a92ba4ba75e87d947364919688032842265
ms.contentlocale: zh-tw
ms.lasthandoff: 05/10/2017

---

# <a name="create-a-network-installation-of-visual-studio-2017"></a>建立 Visual Studio 2017 的網路安裝

通常，企業系統管理員會針對用戶端工作站部署來建立網路安裝點。 Visual Studio 2017 設計為可讓您將初始安裝檔案連同所有產品更新都儲存在單一資料夾 (有時稱為「建立配置」)。如此一來，即使用戶端工作站尚未更新到最新的維護更新，也能使用相同的網路位置來管理其安裝。

> [!NOTE]
> 如果您的企業內使用了多個 Visual Studio 版本 (例如，同時有 Visual Studio Professional 和 Visual Studio Enteprise)，則必須針對每個版本建立各別的網路安裝共用。

## <a name="download-the-visual-studio-bootstrapper"></a>下載 Visual Studio 啟動載入器
**下載**您要的 Visual Studio 版本。 請務必按一下 [儲存]，然後按一下 [開啟資料夾]。

您的安裝程式可執行檔 (具體而言，即為啟動載入器檔案) 將會符合下列其中一個檔案。

|版本 | 下載|
|-------------|-----------------------|
|Visual Studio Enterprise | [**vs_enterprise.exe**](https://aka.ms/vs/15/release/vs_enterprise.exe) |
|Visual Studio Professional | [**vs_professional.exe**](https://aka.ms/vs/15/release/vs_professional.exe) |
|Visual Studio 社群 | [**vs_community.exe**](https://aka.ms/vs/15/release/vs_community.exe) |

其他支援的啟動載入器包括 [vs_buildtools.exe](https://aka.ms/vs/15/release/vs_buildtools.exe)、[vs_feedbackclient.exe](https://aka.ms/vs/15/release/vs_feedbackclient.exe)、[vs_teamexplorer.exe](https://aka.ms/vs/15/release/vs_teamexplorer.exe)、[vs_testagent.exe](https://aka.ms/vs/15/release/vs_testagent.exe)、[vs_testcontroller.exe](https://aka.ms/vs/15/release/vs_testcontroller.exe) 及 [vs_testprofessional.exe](https://aka.ms/vs/15/release/vs_testprofessional.exe)。

## <a name="create-an-offline-installation-folder"></a>建立離線安裝資料夾
若要建立包含所有語言和所有功能的離線安裝，請下列範例中的其中一個命令。

(請確定您是從 [下載] 目錄執行命令。 通常在執行 Windows 10 的電腦上，這會是 `C:\Users\<username>\Downloads`)。

- 針對 Visual Studio Enterprise，請執行：
  ```
  vs_enterprise.exe --layout c:\vs2017offline
  ```
- 針對 Visual Studio Professional，請執行：
  ```
  vs_professional.exe --layout c:\vs2017offline
  ```
- 針對 Visual Studio Community，請執行：
  ```
  vs_community.exe --layout c:\vs2017offline
  ```

## <a name="modify-the-responsejson-file"></a>修改 response.json 檔案
您可以修改 response.json，以設定安裝程式執行時要使用的預設值。  例如，您可以設定 `response.json` 檔案來自動選取所選的一組特定工作負載。
如需詳細資訊，請參閱[使用回應檔自動安裝 Visual Studio](automated-installation-with-response-file.md)。

## <a name="copy-the-layout-to-a-network-share"></a>將配置複製到網路共用

在網路共用上裝載配置，以便能夠從其他電腦執行。
* 範例：<br>
```xcopy /e c:\vs2017offline \\server\products\VS2017```
    
## <a name="customizing-the-network-layout"></a>自訂網路配置
有數個選項可供您用來自訂網路配置。 您可以建立部分配置，以便只包含一組特定[語言地區設定](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)、[工作負載、元件，及其建議或選擇性相依性](workload-and-component-ids.md)。 如果您知道只會將一部分工作負載部署到用戶端工作站，則這會非常有用。 自訂配置的一般命令列參數包括：

 - ```--add``` 可指定[工作負載或元件識別碼](workload-and-component-ids.md)。  若使用 `--add`，則只會下載使用 `--add` 指定的工作負載和元件。  若未使用 `--add`，則會下載所有工作負載和元件。
 - ```--includeRecommended``` 可包含指定工作負載識別碼的所有建議元件
 - ```--includeOptional``` 可包含指定工作負載識別碼的所有建議和選擇性元件。
 - ```--lang``` 可指定[語言地區設定](use-command-line-parameters-to-install-visual-studio.md#list-of-language-locales)。
 
下列範例示範如何建立自訂部分配置。

 - 若要下載僅適用於一種語言的所有工作負載和元件，請執行： <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US```
 - 若要下載適用於多種語言的所有工作負載和元件，請執行： <br>```vs_enterprise.exe --layout C:\vs2017offline --lang en-US de-DE ja-JP```
 - 若要下載適用於所有語言的一個工作負載，請執行： <br> ```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --includeRecommended```
 - 若要下載適用於三種語言的兩個工作負載和一個選擇性元件，請執行： <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended --lang en-US de-DE ja-JP ```
 - 若要下載兩個工作負載及其所有建議元件，請執行： <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeRecommended ```
 - 若要下載兩個工作負載及其所有建議和選擇性原件，請執行： <br>```vs_enterprise.exe --layout C:\vs2017offline --add Microsoft.VisualStudio.Workload.Azure --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Component.GitHub.VisualStudio --includeOptional ```


## <a name="deploying-from-a-network-installation"></a>從網路安裝部署
系統管理員能夠在部分安裝指令碼中，將 Visual Studio 部署到用戶端工作站。 或者，具有系統管理員權限的使用者可以直接從共用執行安裝程式，以在其電腦上安裝 Visual Studio。

- 使用者可以執行如下來安裝： <br>```\\server\products\VS2017\vs_enterprise.exe```
- 系統管理員可以執行如下，以便使用自動模式來安裝： <br>```\\server\products\VS2017\vs_enterprise.exe --quiet --wait --norestart```

> [!TIP]
> 當做為批次檔的一部分執行時，`--wait` 選項可確保 `vs_enterprise.exe` 程序先等候直到安裝完成之後，才會傳回結束代碼。 當企業系統管理員想要在完成的安裝上執行進一步的動作時，此選項非常有用。例如，若要[將產品金鑰套用到成功的安裝](automatically-apply-product-keys-when-deploying-visual-studio.md)， 必須等候安裝完成，才能處理安裝的傳回碼。  若未使用 `--wait`，則 vs_enterprise.exe 程序會在安裝完成之前結束，因此不會傳回代表安裝作業狀態的正確結束代碼。

### <a name="error-codes"></a>錯誤碼
若使用 `--wait` 參數，則 `%ERRORLEVEL%` 環境變數將會根據作業的結果設定為下列其中一個值：

  | **值** | **結果** |
  | --------- | ---------- |
  | 0 | 作業成功完成 |
  | 3010 | 作業成功完成，但安裝需要重新開機才能使用 |
  | 其他 | 發生失敗狀況 - 請檢查記錄檔以取得詳細資訊 |

## <a name="updating-a-network-install-layout"></a>更新網路安裝配置
當產品更新可用時，您可以[更新網路安裝配置](update-a-network-installation-of-visual-studio.md)，以納入更新的套件。

## <a name="how-to-create-a-layout-for-a-previous-visual-studio-2017-release"></a>如何建立舊版 Visual Studio 2017 的配置
**注意**：可在 http://www.visualstudio.com 上取得的 VS 2017 啟動載入器，會自動下載並安裝執行時所能取得的最新版 VS 2017。 如果您今天下載 VS 啟動載入器，並且在 6 個月後執行，它將會安裝 6 個月後可取得的 VS 2017 版本。 如果建立了配置，則從該配置安裝 VS 時，將會安裝存在於該配置中的特定 VS 版本。 即使線上可能有較新的版本，您仍會取得該配置中的 VS 版本。

如果要建立舊版 Visual Studio 2017 的配置，請移至 https://my.visualstudio.com，針對支援的版本下載「固定」版本的 Visual Studio 2017 啟動載入器，這樣您就能建立舊版的網路安裝配置。 

### <a name="how-to-get-support-for-your-offline-installer"></a>如何取得離線安裝程式的支援
如果您的離線安裝發生問題，我們會想要進行了解。 告訴我們的最簡單方式就是使用[回報問題](../ide/how-to-report-a-problem-with-visual-studio-2017.md)工具。 使用此工具時，您可以將我們所需的遙測和記錄檔傳送給我們，來協助我們診斷及修正問題。

我們也提供其他支援選項。 如需這些支援的清單，請參閱[告訴我們](../ide/how-to-report-a-problem-with-visual-studio-2017.md)頁面。

## <a name="see-also"></a>請參閱
* [安裝 Visual Studio](install-visual-studio.md)
* [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
* [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 工作負載與元件識別碼](workload-and-component-ids.md)

