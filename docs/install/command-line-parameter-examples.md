---
title: "Visual Studio 安裝的命令列參數範例 | Microsoft Docs"
ms.custom: 
ms.date: 04/05/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 837F31AA-F121-46e9-9996-F8BCE768E579
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
translationtype: Human Translation
ms.sourcegitcommit: 4e33dc3ebb32569b547aa9bcb6db9a15dbe4fc21
ms.openlocfilehash: ff67313f350264b39151bc0e2f7191ab16300f24
ms.lasthandoff: 04/05/2017

---
# <a name="command-line-parameter-examples-for-visual-studio-2017-installation"></a>Visual Studio 2017 安裝的命令列參數範例
為了說明如何[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)，以下是幾個範例，您可以自訂以符合您的需求。

在每個範例中，`vs_enterprise.exe`、`vs_professional.exe` 和 `vs_community.exe` 表示 Visual Studio 啟動載入器的個別版本，這是起始下載程序的小型檔案 (約 1 MB)。 如果您使用不同的版本，請取代為適當的啟動載入器名稱。

> [!NOTE]
> 所有命令都需要提升系統管理權限，如果未從已提升權限的提示字元啟動程序，則會顯示 [使用者帳戶控制] 提示。

* 安裝 Visual Studio 的最小執行個體，不會顯示互動式提示，但會顯示進度：
```cmd
vs_enterprise.exe --installPath C:\minVS ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --passive --norestart
```

* 使用法文語言套件以無訊息方式安裝 Visual Studio 的桌面執行個體，並只在安裝產品時傳回。
```cmd
vs_enterprise.exe --installPath C:\desktopVS ^
   --addProductLang fr-FR ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --quiet --wait
```

  > [!NOTE]
  >  `--wait` 參數是專為在批次檔中使用所設計。 在批次檔中，直到安裝完成之後，才會繼續執行下一個命令。 `%ERRORLEVEL%` 環境變數會包含命令的傳回值，如[使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md) 頁面中所述。

* 下載 .NET 桌面和 .NET Web 工作負載，以及所有建議的元件和 GitHub 延伸模組。 只包含英文語言套件：
```cmd
vs_community.exe --layout C:\VS2017
   --lang en-US ^
   --add Microsoft.VisualStudio.Workload.CoreEditor ^
   --add Microsoft.VisualStudio.Workload.NetWeb ^
   --add Microsoft.VisualStudio.Workload.ManagedDesktop ^
   --add Microsoft.Net.ComponentGroup.TargetingPacks.Common ^
   --add Microsoft.ComponentGroup.Blend ^
   --add Microsoft.VisualStudio.Component.EntityFramework ^
   --add Microsoft.VisualStudio.Component.DiagnosticTools ^
   --add Microsoft.VisualStudio.Component.DockerTools ^
   --add Microsoft.VisualStudio.Component.CloudExplorer ^
   --add Microsoft.VisualStudio.Component.Wcf.Tooling ^
   --add Component.GitHub.VisualStudio
```

   >[!NOTE]
   Enterprise 版包含這裡未包含的其他建議元件。 如需 Visual Studio Enterprise 中可用的所有建議元件清單，請參閱 [Visual Studio Enterprise 2017 元件目錄](workload-component-id-vs-enterprise.md)。

* 啟動 Visual Studio 2017 Enterprise 版中可用之所有工作負載和元件的互動式安裝：
```cmd
vs_enterprise.exe --all --includeRecommended --includeOptional
```

* 在已安裝 Visual Studio 2017 Community 版的電腦上安裝第二個名為 Visual Studio 2017 Professional 的執行個體，並提供 Node.js 開發的支援：
```cmd
vs_professional.exe --installPath C:\VSforNode ^
   --add Microsoft.VisualStudio.Workload.Node --nickname VSforNode
```

* 從預設安裝的 Visual Studio 執行個體移除程式碼剖析工具元件：
```cmd
vs_enterprise.exe modify ^
   --installPath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise" ^
   --remove Microsoft.VisualStudio.Component.DiagnosticTools ^
   --passive
```

  > [!NOTE]
  >  您可以在命令列結尾處使用 `^` 字元，將多行串連成單一命令。 或者，您也可以直接將這幾行放到一列。

## <a name="see-also"></a>請參閱

 * [Visual Studio 系統管理員指南](visual-studio-administrator-guide.md)
 * [使用命令列參數安裝 Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
 * [建立 Visual Studio 2017 的離線安裝](create-an-offline-installation-of-visual-studio.md)

