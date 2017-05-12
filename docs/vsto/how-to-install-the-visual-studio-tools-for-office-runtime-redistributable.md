---
title: "如何：安裝 Visual Studio Tools for Office Runtime 可轉散發套件"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "在 Visual Studio 中安裝 Office 開發工具"
  - "Office Runtime [Visual Studio 中的 Office 程式開發]"
ms.assetid: ac7a9ad3-e810-4d7f-a0e2-9992c9036b8d
caps.latest.revision: 94
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 93
---
# 如何：安裝 Visual Studio Tools for Office Runtime 可轉散發套件
  若要在 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 中執行使用 Microsoft Office Developer Tools 所建立的方案，則必須先在每部電腦上安裝 Visual Studio 2010 Tools for Office Runtime。  當您安裝 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 和 Microsoft Office 時，此執行階段會自動安裝。  如需詳細資訊，請參閱 [Visual Studio Tools for Office Runtime 安裝案例](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)。  
  
 在下列情況下，您可能需要遵循手動安裝指示：  
  
-   您需要在伺服器上安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。  例如，您想要使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別管理伺服器上的文件層級方案。  
  
-   您需要在已安裝所有其他 Office 方案必要條件的電腦上安裝執行階段。  
  
    > [!NOTE]  
    >  您必須是開發電腦上的系統管理員，才能安裝 .NET Framework 和 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。  
  
### 安裝 Visual Studio Tools for Office Runtime  
  
1.  請安裝 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本。  
  
    -   若要下載 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]，請參閱 [Microsoft .NET Framework 4 \(Web 安裝程式\)](http://go.microsoft.com/fwlink/?LinkId=178957)。  
  
    -   若要下載 [!INCLUDE[net_client_v40_long](../vsto/includes/net-client-v40-long-md.md)]，請參閱 [Microsoft .NET Framework 4 Client Profile \(Web 安裝程式\)](http://go.microsoft.com/fwlink/?LinkId=178958)。  
  
    -   若要下載 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]，請參閱 [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653)。  
  
2.  執行 vstor\_redist.exe 以安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]。  
  
     您可以從 [Visual Studio 2010 Tools for Office Runtime](http://go.microsoft.com/fwlink/?LinkId=140384) 下載這些設定檔案。  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 的必要條件符合 .NET Framework 的必要條件。  
  
     [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 包含語言套件。  如果您的 Windows 安裝設定為英文以外的語言，您可以使用在 Windows 上的相同語言顯示執行階段訊息。  同樣地，如果使用者安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]，然後在安裝設定為英文以外之語言的 Windows 上執行您的方案，則執行階段訊息會以和 Windows 使用的相同語言顯示。  在某些情況下，您可能需要額外的語言套件。  例如，如果您的 Windows 複本使用一個以上的語言設定，或者在您已安裝 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 之後切換至其他語言，則您可能需要其他語言套件。  您可以在 [Microsoft Visual Studio 2010 Tools for Microsoft Office 系統語言套件 \(4.0 版 Runtime\)](http://go.microsoft.com/fwlink/?LinkId=140386) 找到語言套件。  
  
## 請參閱  
 [使用者入門 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [設定電腦以開發 Office 方案](../vsto/configuring-a-computer-to-develop-office-solutions.md)   
 [如何：設定電腦來開發 Office 方案](../vsto/how-to-configure-a-computer-to-develop-office-solutions.md)   
 [如何：安裝 Office 主要 Interop 組件](../vsto/how-to-install-office-primary-interop-assemblies.md)   
 [使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)  
  
  