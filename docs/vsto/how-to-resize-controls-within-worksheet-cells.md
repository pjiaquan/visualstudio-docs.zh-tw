---
title: "如何：在工作表儲存格中調整控制項的大小"
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
  - "控制項 [Visual Studio 中的 Office 程式開發], 調整大小"
  - "Managed 控制項, 調整大小"
  - "Windows Form 控制項 [Visual Studio 中的 Office 程式開發], 調整大小"
  - "工作表, 調整大小"
ms.assetid: 1439db4a-e64b-4381-a6e6-605ba94db3de
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 如何：在工作表儲存格中調整控制項的大小
  當您在工作表上調整資料行或資料列大小時，儲存格中所含的任何主控制項，會自動調整為調整過大小之儲存格的高度或寬度。  Windows Form 控制項預設不會自動重新調整大小。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 如果您在設計階段加入控制項，則必須為每個控制項設定位置選項。  
  
 如果以程式設計的方式加入 Windows Form 控制項，並提供範圍引數，當調整範圍內的儲存格大小時，控制項也會自動調整大小。  如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
## 在設計階段調整控制項大小  
  
#### 若要在設計階段使控制項隨儲存格調整大小  
  
1.  將 Windows Form 控制項從 \[**工具箱**\] 拖曳到工作表。  
  
2.  以滑鼠右鍵按一下該控制項，然後按一下 \[**控制項格式**\]。  
  
3.  在 \[**控制項格式**\] 對話方塊中，按一下 \[**屬性**\] 索引標籤。  
  
4.  在 \[**物件位置**\] 底下，選取 \[**移動和調整儲存格大小**\] 選項，然後按一下 \[**確定**\]。  
  
     當您調整包含控制項的儲存格大小時，控制項也會調整大小以符合儲存格。  
  
## 在執行階段調整控制項大小  
 如果您在執行階段加入 Windows Form 控制項，並傳入 <xref:Microsoft.Office.Interop.Excel.Range> 做為控制項的位置，當調整包含範圍的工作表儲存格大小時，控制項也會自動調整大小。  
  
#### 若要在執行階段使控制項隨儲存格調整大小  
  
1.  將控制項加入至範圍 A1。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#5)]  
  
     當您調整包含控制項的儲存格大小時，控制項也會調整大小以符合儲存格。  
  
## 重設控制項位置  
 您可將 `Placement` 屬性設定為下列 <xref:Microsoft.Office.Interop.Excel.XlPlacement> 值的其中一個，以重設控制項的位置並調整其大小：  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>  
  
-   <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>  
  
#### 若要變更控制項的行為使其不會隨儲存格調整大小或移動  
  
1.  呼叫控制項的位置屬性，並將值設定為 <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>。  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#6)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#6)]  
  
## 請參閱  
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [如何：將 Windows Form 控制項加入至 Office 文件](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [如何：列印時隱藏工作表的控制項](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)   
 [在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Office 文件上的 Windows Form 控制項限制](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  