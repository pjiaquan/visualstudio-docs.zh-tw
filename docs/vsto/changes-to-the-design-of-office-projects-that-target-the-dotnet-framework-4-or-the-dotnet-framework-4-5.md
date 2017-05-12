---
title: "變更以 .NET Framework 4 或 .NET Framework 4.5 為目標的 Office 專案設計 | Microsoft Docs"
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
  - "Visual Studio 中的 Office 程式開發，新功能"
  - "新功能 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 290f5cb4-e2ee-4ed8-987c-2f013405cee9
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 變更以 .NET Framework 4 或 .NET Framework 4.5 為目標的 Office 專案設計
  從 [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] 開始，Visual Studio 導入了一些以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的 Office 專案的設計變更。 如果您熟悉舊版 Visual Studio 中的 Office 專案，在您開發以 .NET Framework 4.0 或更新版本為目標的 Office 專案之前，就該意識到這些變更。 使用 Visual Studio 2013 或更新版本建立的所有專案，預設目標都是 .NET Framework 4.0 或更新版本。  
  
 下列章節描述這些 Office 專案的設計變更。  
  
## 了解 Visual Studio 2010 Tools for Office Runtime 的介面型設計  
 當您開發以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的 Office 專案時，您在 Visual Studio 2010 Tools for Office Runtime 使用的大部分類型都是介面。 對舊版 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 而言是一項重大變更，舊版中這些類型都是類別。 例如，如果您以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標，則 <xref:Microsoft.Office.Tools.Excel.Worksheet> 和 <xref:Microsoft.Office.Tools.Word.Document> 類型就會是介面，而不是類別。 如需詳細資訊，請參閱[Visual Studio Tools for Office Runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)。  
  
 在舊版 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 中可以直接具現化的任何類型，現在都是使用 Globals.Factory 物件的方法，取得這些類型的執行個體。 例如，若要取得實作 <xref:Microsoft.Office.Tools.Excel.SmartTag> 介面的物件，請使用 Globals.Factory.CreateSmartTag 方法。 如需詳細資訊，請參閱下列主題：  
  
-   [更新您要移轉至 .NET Framework 4 或 .NET Framework 4.5 的 Excel 和 Word 專案](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [更新您要移轉至 .NET Framework 4 或 .NET Framework 4.5 之 Office 專案中的功能區自訂](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [更新您要移轉至 .NET Framework 4 或 .NET Framework 4.5 之 Outlook 專案中的表單區域](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
### Office 專案中的新基底類別  
 Visual Studio 2010 Tools for Office Runtime 的新介面型設計，影響了 Office 專案中的產生的類別，例如 `ThisDocument`、`ThisWorkbook` 和 `ThisAddIn`。 以 .NET Framework 3.5 和舊版 Framework 為目標的 Office 專案中，這些產生的類別衍生自 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 類別，例如 Microsoft.Office.Tools.Word.DocumentMicrosoft.Office.Tools.Excel.Worksheet 和 Microsoft.Office.Tools.AddIn。 在以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的專案中，這些 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 類別現在都是介面。 因此，Office 專案中產生的類別不會再衍生出實作。 反而是產生的類別衍生自新的基底類型，例如 <xref:Microsoft.Office.Tools.Word.DocumentBase><xref:Microsoft.Office.Tools.Excel.WorksheetBase> 和 <xref:Microsoft.Office.Tools.AddInBase>。 如需詳細資訊，請參閱[VSTO 增益集程式設計](../vsto/programming-vsto-add-ins.md)與[文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)。  
  
 基底類別不屬於 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 可轉散發套件。 它們反而是定義在隨附於 Visual Studio 的公用程式組件中。 這些組件會在您建置 Office 專案時複製到輸出資料夾，而且必須與方案一起部署。 如需公用程式組件的詳細資訊，請參閱 [Visual Studio Tools for Office Runtime 的組件](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)。  
  
## 重新以 .NET Framework 4 為目標的 Office 專案重大變更  
 下表列出重新以 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或更新版本為目標的 Office 專案中會出現的主要重大變更。 如需詳細資訊，請參閱 [將 Office 方案移轉至 .NET Framework 4 或更新版本](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)。  
  
|重大變更|結果|  
|----------|--------|  
|Office 專案不再使用或支援 <xref:System.Security.SecurityTransparentAttribute>。|您必須從 Office 專案的 AssemblyInfo 程式碼檔案中移除這個屬性，此 Office 專案係從 Visual Studio 2008 升級。 如需詳細資訊，請參閱[移轉至 .NET Framework 4 或 .NET Framework 4.5 的 Office 專案在執行前所必須進行的變更](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|Excel 專案不再使用或支援 ExcelLocale1033Attribute。|您必須從 Excel 專案的 AssemblyInfo 程式碼檔案中移除這個屬性。 如需詳細資訊，請參閱[更新您要移轉至 .NET Framework 4 或 .NET Framework 4.5 的 Excel 和 Word 專案](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|\[功能區 \(視覺化設計工具\)\] 專案項目的程式設計模型已變更。|專案中所有功能區項目的程式碼後置檔案都必須修改。 您也必須修改在執行階段具現化功能區控制項的所有程式碼、處理功能區事件，或以程式設計方式設定功能區元件的位置。 如需詳細資訊，請參閱[更新您要移轉至 .NET Framework 4 或 .NET Framework 4.5 之 Office 專案中的功能區自訂](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|Outlook 表單區域的程式設計模型已變更。|專案中所有表單區域的程式碼後置檔案，以及會在執行階段具現化特定表單區域類別的程式碼，都必須修改。 如需詳細資訊，請參閱[更新您要移轉至 .NET Framework 4 或 .NET Framework 4.5 之 Outlook 專案中的表單區域](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|Excel 和 Word 專案的智慧標籤程式設計模型已變更。 智慧標籤在 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] 和 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] 中已被取代。|如果方案使用智慧標籤，當您建置專案時，就會發生錯誤。 因為 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] 和 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)] 中的智慧標籤已被取代，您必須先移除標籤，才能測試和偵錯 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 或更新版本中的方案。|  
|GetVstoObject 和 HasVstoObject 方法的語法已變更。|當您從主要 Interop 組件 \(PIA\) 的原生物件上存取方法時，您必須將 Globals.Factory 物件傳遞給這些方法；或者也可以在專案的 Globals.Factory 屬性傳回的物件上，存取這些方法。 如需詳細資訊，請參閱[更新您要移轉至 .NET Framework 4 或 .NET Framework 4.5 的 Excel 和 Word 專案](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|Word 內容控制項的事件與新的委派相關聯。|您必須修改處理 Word 內容控制項事件的所有程式碼，以指定新的委派。 如需詳細資訊，請參閱[更新您要移轉至 .NET Framework 4 或 .NET Framework 4.5 的 Excel 和 Word 專案](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|OLEObject 和 OLEControl 類別已重新命名。|您必須修改使用這些類別執行個體的所有程式碼，以改用 <xref:Microsoft.Office.Tools.Excel.ControlSite> 或 <xref:Microsoft.Office.Tools.Word.ControlSite> 物件。 如需詳細資訊，請參閱[更新您要移轉至 .NET Framework 4 或 .NET Framework 4.5 的 Excel 和 Word 專案](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)。|  
|主項目類別，例如 `ThisWorkbook``Sheet`*n*、`ThisDocument` 和 `ThisAddIn`，不再提供可以覆寫的 Dispose 方法。|您必須移動覆寫主項目類別中 Shutdown 事件處理常式的 Dispose 方法中的所有程式碼 \(例如，`ThisAddIn_Shutdown`\)，並移除從主項目類別覆寫的 Dispose 方法。|  
  
## 請參閱  
 [將 Office 方案移轉至 .NET Framework 4 或更新版本](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Office 程式開發的新功能](http://msdn.microsoft.com/zh-tw/bf054af2-c896-4723-aa15-6381145b14bb)   
 [Visual Studio Tools for Office Runtime 概觀](../vsto/visual-studio-tools-for-office-runtime-overview.md)  
  
  