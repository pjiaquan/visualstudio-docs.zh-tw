---
title: "如何：列印時隱藏工作表的控制項 | Microsoft Docs"
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
  - "控制項 [Visual Studio 中的 Office 程式開發], 列印時隱藏"
  - "列印 [Visual Studio 中的 Office 程式開發], 隱藏控制項"
  - "列印 [Visual Studio 中的 Office 程式開發], 工作表"
  - "工作表, 列印時隱藏控制項"
ms.assetid: a637fe9a-9de1-4162-8ff6-fe28ccd62389
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 28
---
# 如何：列印時隱藏工作表的控制項
  列印包含 Windows Form 控制項的 Microsoft Office Excel 文件時，控制項會出現在列印的工作表上，  您可以在列印工作表時隱藏控制項。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  如果您隱藏顯示資料的控制項 \(例如 <xref:Microsoft.Office.Tools.Excel.Controls.TextBox>\)，則在列印的工作表上無法看到控制項中的資料。  
  
> [!NOTE]  
>  在下列指示的某些 Visual Studio 使用者介面項目中，您的電腦可能會顯示不同的名稱或位置：  您所擁有的 Visual Studio 版本和使用的設定決定了這些項目。  如需詳細資訊，請參閱[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/zh-tw/22c4debb-4e31-47a8-8f19-16f328d7dcd3)。  
  
### 若要在列印工作表時隱藏控制項  
  
1.  在 Visual Studio 中建立或開啟 Excel 專案，然後確認設計工具中可以看見 \[**Sheet1**\]。  如需建立專案的詳細資訊，請參閱 [如何：在 Visual Studio 中建立 Office 專案](../vsto/how-to-create-office-projects-in-visual-studio.md)。  
  
2.  從 \[**工具箱**\] 的 \[**通用控制項**\] 索引標籤，將 <xref:Microsoft.Office.Tools.Excel.Controls.Button> 控制項拖曳至 `Sheet1` 上的儲存格。  
  
3.  在 \[**屬性**\] 視窗中，將 <xref:Microsoft.Office.Tools.Excel.Controls.Button.PrintObject%2A> 屬性設定為 **False**。  
  
## 請參閱  
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [Office 文件上的 Windows Forms 控制項概觀](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [如何：將 Windows Form 控制項加入至 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [如何：在工作表儲存格中調整控制項的大小](../vsto/how-to-resize-controls-within-worksheet-cells.md)  
  
  