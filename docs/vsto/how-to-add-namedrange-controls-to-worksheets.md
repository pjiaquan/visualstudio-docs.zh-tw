---
title: "如何：將 NamedRange 控制項加入至工作表 | Microsoft Docs"
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
  - "範圍，加入工作表"
  - "NamedRange 控制項，加入工作表"
  - "控制項 [Visual Studio 中的 Office 程式開發]，加入工作表"
ms.assetid: da7ec48f-92cb-4fa3-b3e2-447c238d17a8
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# 如何：將 NamedRange 控制項加入至工作表
  您可以在文件層級專案中，於設計階段和執行階段將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入 Microsoft Office Excel 工作表。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 您也可以在 VSTO 增益集專案中，於執行階段加入 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項。  
  
 本主題說明下列工作：  
  
-   [在設計階段加入 NamedRange 控制項](#designtime)  
  
-   [在文件層級專案中，於執行階段加入 NamedRange 控制項](#runtimedoclevel)  
  
-   [在 VSTO 增益集專案中，於執行階段加入 NamedRange 控制項](#runtimeaddin)  
  
 如需 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項的詳細資訊，請參閱 [NamedRange 控制項](../vsto/namedrange-control.md)。  
  
##  <a name="designtime"></a> 在設計階段加入 NamedRange 控制項  
 有幾種方式可在文件層級專案中，於設計階段將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入工作表：在 Excel 中、透過 Visual Studio 的 \[工具箱\]，以及透過 \[資料來源\] 視窗。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
#### 使用 Excel 中的名稱方塊將 NamedRange 控制項加入工作表  
  
1.  選取您要包含在指定範圍中的一或多個儲存格。  
  
2.  在 \[名稱方塊\] 中，輸入範圍的名稱，然後按 ENTER 鍵。  
  
     \[名稱方塊\] 位於工作表 **A** 欄正上方的公式列旁。  
  
#### 使用工具箱將 NamedRange 控制項加入工作表  
  
1.  開啟 \[工具箱\]，然後按一下 \[Excel 控制項\] 索引標籤。  
  
2.  按一下 <xref:Microsoft.Office.Tools.Excel.NamedRange> 並將拖曳至工作表。  
  
     \[加入指定範圍\] 對話方塊隨即出現。  
  
3.  選取您要包含在指定範圍中的一或多個儲存格。  
  
4.  按一下 \[**確定**\]。  
  
     如果您不想要使用指定給控制項的預設名稱，您可以在 \[屬性\] 視窗中變更名稱。  
  
#### 使用資料來源視窗將 NamedRange 控制項加入工作表  
  
1.  開啟 \[資料來源\] 視窗並為您的專案建立資料來源。 如需詳細資訊，請參閱[如何：連接至資料庫中的資料](~/data-tools/how-to-connect-to-data-in-a-database.md)。  
  
2.  將單一欄位從 \[資料來源\] 視窗拖曳至您的工作表。  
  
     資料繫結 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項隨即加入工作表。 如需詳細資訊，請參閱[資料繫結和 Windows Form](http://msdn.microsoft.com/library/419aac5e-819b-4aad-88b0-73a2f8c0bd27)。  
  
##  <a name="runtimedoclevel"></a> 在文件層級專案中，於執行階段加入 NamedRange 控制項  
 您可以在執行階段，以程式設計方式將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入工作表。 如此可讓您建立主控制項，以回應事件。 當工作表關閉時，動態建立的指定範圍不會保存為工作表中的主控制項。 如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### 以程式設計方式將 NamedRange 控制項加入工作表  
  
1.  在 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件處理常式中插入下列程式碼，以將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入儲存格 **A1** 並將其 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 屬性設定為 `Hello world!`  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#3)]
     [!code-vb[Trin_VstcoreHostControlsExcel#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#3)]  
  
##  <a name="runtimeaddin"></a> 在 VSTO 增益集專案中，於執行階段加入 NamedRange 控制項  
 您可以在 VSTO 增益集專案中，以程式設計方式將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入任何開啟的工作表。 當工作表關閉時，動態建立的指定範圍不會保存為工作表中的主控制項。 如需詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
#### 以程式設計方式將 NamedRange 控制項加入工作表  
  
1.  下列程式碼會產生以開啟的工作表為基礎的工作表主項目，然後將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項加入儲存格 **A1** 並將其 <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> 屬性設定為 `Hello world`。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#7)]
     [!code-vb[Trin_Excel_Dynamic_Controls#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#7)]  
  
## 請參閱  
 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [NamedRange 控制項](../vsto/namedrange-control.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [如何：調整 NamedRange 控制項的大小](../vsto/how-to-resize-namedrange-controls.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  