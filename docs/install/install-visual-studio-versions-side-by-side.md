---
title: "並存安裝 Visual Studio 版本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "並存安裝 [Visual Studio]"
  - "說明 [Visual Studio]，安裝"
  - "Express 版 [Visual Studio]"
ms.assetid: 4d00f240-4910-4699-aaf3-cda6461f0c29
caps.latest.revision: 48
caps.handback.revision: 47
author: "TerryGLee"
ms.author: "tglee"
manager: "ghogen"
---
# 並存安裝 Visual Studio 版本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可將此版本的 Visual Studio 安裝在已安裝舊版的電腦上。 如果您遇到安裝失敗的情況，您可以使用[記錄收集工具](http://go.microsoft.com/fwlink/?LinkId=262077)收集失敗的資訊，讓您可以偵錯問題。  
  
> [!NOTE]
>  我們建議您以發行的順序來安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 版本。 例如，請先安裝 Visual Studio 2013，再安裝 Visual Studio 2015。  
  
 並存安裝多個版本之前，請先檢閱下列狀況：  
  
-   如果您使用 Visual Studio 2015 開啟 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 所建立的方案，只要未實作 Visual Studio 2015 特定的任何功能，稍後就可以在舊版中開啟和修改該方案。  
  
-   如果您嘗試使用 Visual Studio 2015 開啟 [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] 或以前版本所建立的方案，可能需要修改專案和檔案，才能與 Visual Studio 2015 相容。 如需詳細資訊，請參閱[移植、移轉和升級 Visual Studio 專案](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)。  
  
-   如果在已經安裝多個 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的電腦上解除安裝其中一個版本，則會移除所有版本的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 檔案關聯。 您可以使用[選項](../ide/reference/general-environment-options-dialog-box.md)對話方塊中，位於 \[環境\] 的 \[一般\] 頁面上的 \[還原檔案關聯\] 按鈕來重新對應這些檔案關聯。  
  
-   Visual Studio 不會自動升級擴充功能，因為並非所有擴充功能都相容。 您必須從 [Visual Studio 組件庫](http://go.microsoft.com/fwlink/?LinkId=178891)或軟體發行者重新安裝擴充功能。  
  
## .NET Framework 的版本和並存安裝  
  
-   Visual Basic、Visual C\# 或 Visual F\# 專案中 \[專案設計工具\] 使用 \[目標 Framework\] 選項，指定專案的目標 .NET Framework 版本。 對於 C\+\+ 專案，您可以手動修改 .vcxproj 檔案來變更目標 Framework。 如需詳細資訊，請參閱 [版本相容性](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md)。  
  
     當您建立專案時，您可以在 \[新增專案\] 對話方塊的 \[.NET Framework\] 清單中指定專案的目標 .NET Framework 版本。  
  
     如需語言特定的資訊，請參閱下表中適當的主題。  
  
    |語言|主題|  
    |--------|--------|  
    |[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]|[應用程式頁面，專案設計工具 \(Visual Basic\)](../ide/reference/application-page-project-designer-visual-basic.md)|  
    |Visual C\#|[專案設計工具，應用程式頁 \(C\#\)](../ide/reference/application-page-project-designer-csharp.md)|  
    |Visual F\#|[Configuring Projects](../Topic/Configuring%20Projects%20\(F%23\).md)|  
    |C\+\+|[如何：修改目標 Framework 和平台工具組](../Topic/How%20to:%20Modify%20the%20Target%20Framework%20and%20Platform%20Toolset.md)|  
    |[!INCLUDE[jsprjscript](../extensibility/debugger/includes/jsprjscript_md.md)]|[在舊版的通用語言執行平台上執行 JScript 應用程式](http://msdn.microsoft.com/zh-tw/bbea51b5-ac03-4e6c-b9a6-f487ef63eda5)|  
  
## 請參閱  
 [安裝 Visual Studio](../Topic/Installing%20Visual%20Studio%202015.md)   
 [移植、移轉和升級 Visual Studio 專案](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)   
 [版本相容性](../Topic/Version%20Compatibility%20in%20the%20.NET%20Framework.md)   
 [安裝多個語言版本的 Visual Studio](../Topic/Installing%20Multiple%20Language%20Versions%20of%20Visual%20Studio.md)   
 [建置 C\/C\+\+ 隔離應用程式和並存組件](/visual-cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies)   
 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)