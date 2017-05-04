---
title: "Workbook 主項目 | Microsoft Docs"
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
  - "Excel 活頁簿"
  - "活頁簿主項目"
  - "主項目 [Visual Studio 中的 Office 程式開發]，活頁簿"
  - "活頁簿，Excel"
  - "Workbook 主項目，事件"
  - "活頁簿"
  - "Excel [Visual Studio 中的 Office 程式開發]，活頁簿"
  - "活頁簿，事件"
  - "事件 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 54489d91-a799-4dc2-89b8-498cf17c2f57
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Workbook 主項目
  <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目是可從 Excel 的主要 Interop 組件擴充 <xref:Microsoft.Office.Interop.Excel.Workbook> 類型的一種類型。<xref:Microsoft.Office.Tools.Excel.Workbook> 主項目除了提供與 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件相同的所有屬性、方法和事件之外，也會提供其他功能。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 文件層級專案中有代表專案中活頁簿的預設 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目。 在 VSTO 增益集專案中，您可以在執行階段產生 <xref:Microsoft.Office.Tools.Excel.Workbook>主項目。  
  
## 了解文件層級專案中的 Workbook 主項目  
 若要存取專案中的活頁簿，請使用 `ThisWorkbook` 類別。`ThisWorkbook` 類別可讓您存取 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目的成員，以在自訂中執行基本工作，例如在開啟或關閉活頁簿時執行程式碼。 如需詳細資訊，請參閱[文件層級自訂程式設計](../vsto/programming-document-level-customizations.md)。  
  
 `ThisWorkbook` 類別提供了一個位置，供您開始在專案中撰寫程式碼。 由於該類別會提供與 Excel 之主要 Interop 組件中的 <xref:Microsoft.Office.Interop.Excel.Workbook> 物件相同的所有屬性、方法和事件，因此您也可以使用 `ThisWorkbook` 存取 Excel 的物件模型。 如需詳細資訊，請參閱[Excel 物件模型概觀](../vsto/excel-object-model-overview.md)。  
  
 按兩下 \[方案總管\] 中的 \[ThisWorkbook\] 專案項目以顯示活頁簿設計工具，並在 \[屬性\] 視窗中檢視活頁簿的屬性和事件。  
  
### 文件層級專案中 Workbook 主項目的限制  
 文件層級專案只能包含一個 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目 \(也就是 `ThisWorkbook` 類別\)。 您無法在設計階段將新的 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目加入專案，也無法在執行階段從文件層級自訂建立新的 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目。  
  
 如果您在執行階段建立新的 Excel 活頁簿，該活頁簿會是 <xref:Microsoft.Office.Interop.Excel.Workbook> 類型。 由於這不是主項目，因此無法包含任何主控制項或 Windows Form 控制項。 如需在執行階段建立活頁簿的詳細資訊，請參閱[如何：以程式設計方式建立新活頁簿](../vsto/how-to-programmatically-create-new-workbooks.md)。  
  
 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目不能做為主控制項的容器。 因此，您無法將任何可見的控制項加入活頁簿，但您可以加入 <xref:System.Data.DataSet> 等元件，讓所有工作表都能共用這些元件。 在文件層級專案中，您可以在 \[工具箱\] 的 \[元件\] 索引標籤、\[資料\] 索引標籤和 \[所有 Windows Forms\] 索引標籤上，找到活頁簿可用的元件。  
  
> [!NOTE]  
>  Visual Studio 中的 Office 開發工具不支援共用活頁簿。  
  
## 了解 VSTO 增益集專案中的 Workbook 主項目  
 在 VSTO 增益集專案中，您可以在執行階段為使用 Excel 開啟的任何活頁簿產生 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目。 若要產生 <xref:Microsoft.Office.Tools.Excel.Workbook> 主項目，請使用 GetVstoObject 方法。 如需詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
## 請參閱  
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [Worksheet 主項目](../vsto/worksheet-host-item.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  