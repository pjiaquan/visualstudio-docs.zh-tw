---
title: "全域存取 Office 專案中的物件 | Microsoft Docs"
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
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "全域類別，物件全域存取權"
  - "工作表 [Visual Studio 中的 Office 程式開發]，全域存取權"
  - "文件 [Visual Studio 中的 Office 程式開發]，全域存取權"
  - "事件處理常式 [Visual Studio 中的 Office 程式開發]"
  - "ThisWorkbook_Startup"
  - "應用程式層級增益集 [Visual Studio 中的 Office 程式開發]"
  - "增益集 [Visual Studio 中的 Office 程式開發]，事件"
  - "活頁簿 [Visual Studio 中的 Office 程式開發]，全域存取權"
  - "ThisWorkbook_Shutdown"
  - "文件層級自訂 [Visual Studio 中的 Office 程式開發]"
  - "Startup 事件"
  - "Shutdown 事件"
  - "專案 [Visual Studio 中的 Office 程式開發]，全域存取權"
  - "Office 文件 [Visual Studio 中的 Office 程式開發]，全域存取權"
  - "ThisAddin_Startup"
  - "事件 [Visual Studio 中的 Office 程式開發]"
  - "ThisAddIn_Shutdown"
ms.assetid: f6a7f0ef-75d0-4a9b-9aec-be95ffa26adf
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# 全域存取 Office 專案中的物件
  當您建立 Office 專案時，Visual Studio 會在專案中自動產生名為 `Globals` 的類別。 您可以使用 `Globals` 類別，在執行階段從專案的任何程式碼存取數個不同的專案項目。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## 如何使用 Globals 類別  
 `Globals` 是靜態類別，會將某些項目的參考保留在專案中。 您可以使用 `Globals` 類別，在執行階段從專案的任何程式碼存取下列項目：  
  
-   Excel 活頁簿或範本專案中的 `ThisWorkbook` 和  `Sheet`*n* 類別。 您可以使用 `Globals.ThisWorkbook` 和  `Sheet`*n* 屬性來存取這些物件。  
  
-   Word 文件或範本專案中的 `ThisDocument` 類別。 您可以使用 `Globals.ThisDocument` 屬性來存取這個物件。  
  
-   VSTO 增益集專案中的 `ThisAddIn` 類別。 您可以使用 `Globals.ThisAddIn` 屬性來存取這個物件。  
  
-   專案中使用 \[功能區設計工具\] 自訂的所有功能區。 您可以使用 `Globals.Ribbons` 屬性來存取功能區。 如需詳細資訊，請參閱[在執行階段存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)。  
  
-   Outlook VSTO 增益集專案中的所有 Outlook 表單區域。 您可以使用 `Globals.FormRegions` 屬性來存取表單區域。 如需詳細資訊，請參閱[在執行階段存取表單區域](../vsto/accessing-a-form-region-at-run-time.md)。  
  
-   Factory 物件，可讓您在執行階段於 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 或 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 目標專案中建立功能區控制項和主項目。 您可以使用 `Globals.Factory` 屬性來存取這個物件。 這個物件是可實作下列其中一個介面的類別執行個體：  
  
    -   <xref:Microsoft.Office.Tools.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
 例如，您可以使用 `Globals.Sheet1` 屬性在使用者按一下 Excel 文件層級專案中執行窗格上的按鈕時，將文字插入 `Sheet1` 上的 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。  
  
 [!code-csharp[Trin_VstcoreProgramming#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstcoreProgramming#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#1)]  
  
## 初始化 Globals 類別  
 嘗試在文件或 VSTO 增益集完全初始化之前使用 `Globals` 類別的程式碼，可能會擲回執行階段例外狀況。 例如，在宣告類別層級變數時使用 `Globals` 可能會失敗，因為 `Globals` 類別可能不會在宣告的物件具現化之前，使用所有主項目的參考進行初始化。  
  
> [!NOTE]  
>  雖然 `Globals` 類別絕對不會在設計階段初始化，但是設計工具卻會建立控制項執行個體。 這表示如果您建立的使用者控制項會在使用者控制項類別中使用 `Globals` 類別的某個屬性，您必須先檢查該屬性是否傳回 **null**，再嘗試使用傳回的物件。  
  
## 請參閱  
 [在執行階段存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)   
 [在執行階段存取表單區域](../vsto/accessing-a-form-region-at-run-time.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [Document 主項目](../vsto/document-host-item.md)   
 [Workbook 主項目](../vsto/workbook-host-item.md)   
 [Worksheet 主項目](../vsto/worksheet-host-item.md)   
 [撰寫 Office 方案中的程式碼](../vsto/writing-code-in-office-solutions.md)  
  
  