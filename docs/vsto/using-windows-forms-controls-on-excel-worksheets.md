---
title: "在 Excel 工作表中使用 Windows Form 控制項"
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
  - "控制項 [Visual Studio 中的 Office 程式開發], Windows Form 控制項"
  - "Excel [Visual Studio 中的 Office 程式開發], Windows Form 控制項"
  - "Windows Form 控制項 [Visual Studio 中的 Office 程式開發], Excel"
ms.assetid: bbda7461-0d69-4b56-8ba3-418d63ba49db
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 在 Excel 工作表中使用 Windows Form 控制項
  您可以使用將控制項加入至 Windows Form 的相同方式，將 Windows Form 控制項加入至 Microsoft Office Excel 活頁簿。  如需在文件上使用控制項的一般資訊，請參閱 [Office 文件上的 Windows Forms 控制項概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Excel 的控制項考量  
 在 Excel 中，需要特別考量某些事項。  
  
### 將控制項大小調整為儲存格大小  
 您可以將控制項設定為在父儲存格大小變更時，自動調整大小。  如需詳細資訊，請參閱[如何：在工作表儲存格中調整控制項的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)。  
  
### 加入所有工作表共用的元件  
 您可以將想要讓所有工作表共用的元件 \(例如 <xref:System.Data.DataSet>\) 加入至活頁簿設計工具而不是工作表。  元件就會出現在元件匣裡。  
  
### 控制項內嵌公式  
 在 Excel 中選取控制項時，您會在 \[**資料編輯列**\] 看到 \[**\=EMBED\("WinForms.Control.Host",""\)**\]。  這個文字是必要的，不應該刪除。  
  
## 請參閱  
 [如何：在工作表儲存格中調整控制項的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)   
 [如何：列印時隱藏工作表的控制項](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [逐步解說：使用 CheckBox 控制項來變更工作表格式](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)   
 [逐步解說：使用按鈕在工作表的文字方塊中顯示文字](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)   
 [逐步解說：使用選項按鈕更新工作表中的圖表](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)  
  
  