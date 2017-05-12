---
title: "使用 ServerDocument 類別管理伺服器上的文件"
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
  - "文件 [Visual Studio 中的 Office 程式開發], 在伺服器上管理"
  - "Office 文件 [Visual Studio 中的 Office 程式開發], 在伺服器上管理"
  - "ServerDocument 類別, 管理伺服器上的文件"
ms.assetid: 1ac90e89-d07d-4874-9d24-6741d6679a21
caps.latest.revision: 40
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 39
---
# 使用 ServerDocument 類別管理伺服器上的文件
  您可以使用 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 中的 ServerDocument 類別來管理數個文件層級的自訂作業，即使尚未安裝 Microsoft Office Word 和 Microsoft Office Excel 也沒關係。  您可以執行下列工作：  
  
-   存取和修改文件或活頁簿之資料快取中的資料。  如需詳細資訊，請參閱[使用文件中的快取資料](#CachedData)。  
  
-   管理與文件相關聯的自訂組件。  如需詳細資訊，請參閱[管理文件自訂](#CustomizationInfo)。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## 了解 ServerDocument 類別  
 ServerDocument 類別的設計是用於未安裝 Office 的電腦上。  因此，一般您會在未與 Office 整合的應用程式 \(例如主控台專案或 Windows Form 專案，而不是 Office 專案\) 中使用這個類別。  使用 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別在 Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll 組件。  
  
 ServerDocument 類別可用來在使用 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]，建立的文件層級自訂。  
  
 如需 Visual Studio 2010 Tools for Office Runtime 和 Office Extensions for 的更多資訊的 .NET Framework，請參閱 [Visual Studio Tools for Office Runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
> [!NOTE]  
>  如果您在 Visual Studio Tools for Office System \(3.0 版 Runtime\) 使用 ServerDocument 類別的舊版應用程式，在執行應用程式的電腦上安裝 Visual Studio Tools for Office System \(3.0 版 Runtime\)。  Visual Studio 2010 Tools for Office Runtime 無法執行這些應用程式。  
  
##  <a name="CachedData"></a> 使用文件中的快取資料  
 ServerDocument 類別提供的成員可讓您用來處理自訂文件中的資料快取。  如需快取資料的詳細資訊，請參閱[快取資料](../vsto/caching-data.md)和[存取伺服器文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。  
  
 下表列出您可用來處理快取資料的成員。  
  
|工作|使用的成員|  
|--------|-----------|  
|判斷文件是否具有資料快取。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.IsCacheEnabled%2A> 方法。|  
|若要存取文件中的快取資料。<br /><br /> 如需詳細資訊，請參閱[存取伺服器文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> 屬性。|  
  
##  <a name="CustomizationInfo"></a> 管理文件自訂  
 您可以使用 ServerDocument 類別的成員來管理與文件相關聯的自訂組件。  例如，您可以透過程式設計的方式從文件中移除自訂，這樣一來文件就不再屬於自訂的一部分。  
  
 下表列出您可用來管理自訂組件的成員。  
  
|工作|使用的成員|  
|--------|-----------|  
|判斷文件是否屬於文件層級自訂的一部分。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.GetCustomizationVersion%2A> 方法。|  
|若要以程式設計方式在執行階段將自訂附加至文件。<br /><br /> 如需詳細資訊，請參閱[如何：將 Managed 程式碼擴充附加至文件](../vsto/how-to-attach-managed-code-extensions-to-documents.md)。|其中一個 <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.AddCustomization%2A> 方法。|  
|若要以程式設計方式在執行階段從文件中移除自訂。<br /><br /> 如需詳細資訊，請參閱[如何：從文件移除 Managed 程式碼擴充](../vsto/how-to-remove-managed-code-extensions-from-documents.md)。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.RemoveCustomization%2A> 方法。|  
|若要取得與文件關聯之部署資訊清單的 URL。|<xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.DeploymentManifestUrl%2A> 屬性。|  
  
## 請參閱  
 [如何：將 Managed 程式碼擴充附加至文件](../vsto/how-to-attach-managed-code-extensions-to-documents.md)   
 [如何：從文件移除 Managed 程式碼擴充](../vsto/how-to-remove-managed-code-extensions-from-documents.md)   
 [Visual Studio Tools for Office Runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [快取資料](../vsto/caching-data.md)  
  
  