---
title: "Visual Studio Tools for Office Runtime 的組件 | Microsoft Docs"
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
  - "Visual Studio Tools for Office Runtime，組件"
ms.assetid: d2b7f8f4-0f41-4943-bca5-48c520748b7e
caps.latest.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# Visual Studio Tools for Office Runtime 的組件
  當您建立 Office 專案時，Visual Studio 會自動針對專案類型和專案的目標 .NET Framework，加入適用 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 組件的參考。 適用於 .NET Framework 3.5、[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 和 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 的 Office 擴充功能包含不同的組件。 如需 Office 擴充功能的詳細資訊，請參閱 [Visual Studio Tools for Office Runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
## 適用於 .NET Framework 4 和 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 的 Office 擴充功能中的組件  
 下表列出適用於 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 和 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 的 Office 擴充功能隨附的組件。 如需這些組件中之命名空間和類型的相關文件，請參閱 [Managed 參考 &#40;Visual Studio 中的 Office 程式開發&#41;](../vsto/managed-reference-office-development-in-visual-studio.md)。  
  
|組件名稱|描述|  
|----------|--------|  
|Microsoft.Office.Tools.Common.dll|提供下列類型：<br /><br /> -   用於建立功能區自訂和智慧標籤的類型。 **Note:**      智慧標籤在 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] 和 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] 中已被取代。<br />-   用於在文件層級自訂中建立執行窗格，以及在 VSTO 增益集中建立自訂工作窗格的類型。|  
|Microsoft.Office.Tools.Excel.dll|提供代表 Excel 專案之主項目和主控制項的介面，以及支援類型。 如需詳細資訊，請參閱[使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.Outlook.dll|提供可讓您在 Outlook VSTO 增益集中建立自訂表單區域的類型。|  
|Microsoft.Office.Tools.Word.dll|提供代表 Word 專案之主項目和主控制項的介面，以及支援類型。 如需詳細資訊，請參閱[使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.v4.0.Framework.dll|提供下列類型：<br /><br /> -   Visual Studio Tools for Office Runtime 可能擲回的例外狀況。<br />-   建立 Outlook 表單區域時可使用的屬性。|  
|Microsoft.Office.Tools.dll|提供屬於 Visual Studio Tools for Office Runtime 基礎結構，而且不適合直接從程式碼使用的類型。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|提供下列類型：<br /><br /> -   <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 屬性和 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 介面，您可以使用這個屬性和介面來快取文件層級自訂中的資料物件。 如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。<br />-   <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> 介面，您可以實作這個介面來執行額外的安裝步驟，做為 Office 方案之 ClickOnce 安裝程式的最後一個步驟。 如需詳細資訊，請參閱[使用 ClickOnce 部署 Office 方案](../vsto/deploying-an-office-solution-by-using-clickonce.md)。<br />-   Visual Studio Tools for Office Runtime 可能擲回的例外狀況。<br />-   其他屬於 Visual Studio Tools for Office Runtime 基礎結構的一部分且不適合直接使用於您程式碼的型別。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|提供下列類型：<br /><br /> -   <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 類別，您可以使用這個類別將自訂組件附加至文件，並存取文件中的快取資料。 如需詳細資訊，請參閱[使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)。<br />-   代表文件層級自訂中快取資料階層架構的數個類別。 如需詳細資訊，請參閱[存取伺服器文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。|  
  
 以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 為目標的專案還會參考下列組件。 這些組件不是 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可轉散發套件的一部分， 而是必須隨方案一起部署的相依組件。 根據預設，這些組件會複製到專案的組建輸出資料夾 \(當這些組件的 \[複製到本機\] 屬性設定為 \[True\] 時\)。 如果使用 ClickOnce 部署專案，這些組件會包含在產生的套件中。  
  
|組件名稱|描述|  
|----------|--------|  
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|提供 VSTO 增益集專案中產生之 `ThisAddIn` 類別的基底類別，以及所有專案中產生之功能區類別的基底類別。|  
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|提供下列類型：<br /><br /> -   Excel 文件層級專案中產生之 `ThisWorkbook` 和 `Sheet` 類別的基底類別。<br />-   可用於 Excel 專案之工作表的 Windows Form 控制項。|  
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|提供 Outlook 專案中產生之 `ThisAddIn` 和表單區域類別的基底類別。|  
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|提供下列類型：<br /><br /> -   Word 文件層級專案中產生之 `ThisDocument` 類別的基底類別。<br />-   可用於 Word 專案之文件的 Windows Form 控制項。|  
  
## 適用於 .NET Framework 3.5 的 Office 擴充功能中的組件  
 下表列出適用於 .NET Framework 3.5 的 Office 擴充功能隨附的組件。 如需這些組件中之命名空間和類別的相關文件，請參閱 Visual Studio 2008 文件中的下列參考章節：[http:\/\/go.microsoft.com\/fwlink\/?LinkId\=160658](http://go.microsoft.com/fwlink/?LinkId=160658)。  
  
|組件名稱|描述|  
|----------|--------|  
|Microsoft.Office.Tools.Common.v9.0.dll|提供下列類型：<br /><br /> -   VSTO 增益集的 Microsoft.Office.Tools.AddIn 基底類別。<br />-   用於建立功能區自訂和智慧標籤的類別。 **Note:**      智慧標籤在 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] 和 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] 中已被取代。<br />-   用於在文件層級自訂中建立執行窗格，以及在 VSTO 增益集中建立自訂工作窗格的類別。|  
|Microsoft.Office.Tools.Excel.v9.0.dll|提供 Excel 方案的主項目和主控制項。 如需詳細資訊，請參閱[使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.Outlook.v9.0.dll|提供可讓您在 Outlook VSTO 增益集中建立自訂表單區域的類別。|  
|Microsoft.Office.Tools.Word.v9.0.dll|提供 Word 方案的主項目和主控制項。 如需詳細資訊，請參閱[使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)。|  
|Microsoft.Office.Tools.v9.0.dll|提供下列類型：<br /><br /> -   Microsoft.VisualStudio.Tools.Office.RemoteBindableComponent 類別，提供文件層級自訂中主控制項的資料繫結功能。<br />-   其他屬於 Visual Studio Tools for Office Runtime 基礎結構的一部分且不適合直接使用於您程式碼的型別。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|提供下列類型：<br /><br /> -   Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute 屬性和 Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType 介面，您可以使用這個屬性和介面來快取文件層級自訂中的資料物件。 如需詳細資訊，請參閱[快取資料](../vsto/caching-data.md)。<br />-   Visual Studio Tools for Office Runtime 可能擲回的例外狀況。<br />-   其他屬於 Visual Studio Tools for Office Runtime 基礎結構的一部分且不適合直接使用於您程式碼的型別。|  
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|提供 Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction 介面，您可以實作這個介面來執行額外的安裝步驟，做為 Office 方案之 ClickOnce 安裝程式的最後一個步驟。 如需詳細資訊，請參閱[進階 Office 方案部署](http://msdn.microsoft.com/zh-tw/9147b6f6-849f-4cb1-b2c5-e22658d74b02)。|  
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|提供下列類型：<br /><br /> -   Microsoft.VisualStudio.Tools.Applications.ServerDocument 類別，您可以使用這個類別以程式設計方式將自訂組件附加至文件，並存取文件中的快取資料。 如需詳細資訊，請參閱[使用 ServerDocument 類別管理伺服器上的文件](../vsto/managing-documents-on-a-server-by-using-the-serverdocument-class.md)。<br />-   代表文件層級自訂中快取資料階層架構的數個類別。 如需詳細資訊，請參閱[存取伺服器文件中的資料](../vsto/accessing-data-in-documents-on-the-server.md)。|  
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|提供下列類型：<br /><br /> -   Microsoft.VisualStudio.Tools.Office.Runtime.Security.AddInSecurityEntry 和 Microsoft.VisualStudio.Tools.Office.Runtime.Security.UserInclusionList 類別，您可以使用這些類別來建立使用者內含清單項目，將信任授與以 .NET Framework 3.5 為目標的 Office 方案。<br />-   其他屬於 Visual Studio Tools for Office Runtime 基礎結構，但不適合直接從程式碼使用的類型。|  
  
## 請參閱  
 [Visual Studio Tools for Office Runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)   
 [Visual Studio Tools for Office Runtime 安裝案例](../vsto/visual-studio-tools-for-office-runtime-installation-scenarios.md)  
  
  