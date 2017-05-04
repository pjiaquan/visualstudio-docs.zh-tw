---
title: "如何：將圖表控制項加入至工作表 | Microsoft Docs"
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
  - "圖表控制項 [Visual Studio 中的 Office 程式開發], 加入至工作表"
  - "控制項 [Visual Studio 中的 Office 程式開發], 加入至工作表"
ms.assetid: f02568e7-5caa-45b4-aa2a-4f73b0565d4e
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# 如何：將圖表控制項加入至工作表
  您可以在設計階段及執行階段，於文件層級自訂中，將 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項加入 Microsoft Office Excel 工作表。  您也可以在執行階段，於 VSTO 增益集中加入 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項。  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
 本主題說明下列工作：  
  
-   [在設計階段加入圖表控制項](#designtime)  
  
-   [在執行階段於文件層級專案中加入圖表控制項](#runtimedoclevel)  
  
-   [在執行階段於 VSTO 增益集專案中加入圖表控制項](#runtimeaddin)  
  
 如需控制項的詳細資訊<xref:Microsoft.Office.Tools.Excel.Chart>，請參閱[圖表控制項](../vsto/chart-control.md)。  
  
##  <a name="designtime"></a> 在設計階段加入圖表控制項  
 您可以採用您從應用程式中加入圖表的方式，將 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項加入工作表。  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.Chart> 控制項無法從 \[工具箱\] 或 \[資料來源\] 視窗中使用。  
  
#### 將圖表主控制項加入 Excel 工作表  
  
1.  在 \[插入\] 索引標籤的 \[圖表\] 群組中按一下 \[資料行\]，再按一下圖表的類別，然後按一下您需要的圖表類型。  
  
2.  在 \[插入圖表\] 對話方塊中，按一下 \[確定\]。  
  
3.  在 \[設計\] 索引標籤的 \[資料\] 群組中，按一下 \[選取資料\]。  
  
4.  在 \[選取資料來源\] 對話方塊中，按一下 \[圖表資料範圍\] 方塊，然後清除其中的預設選擇。  
  
5.  在 \[圖表的資料\] 工作表中，選取包含圖表資料之資料格的範圍 \(儲存格 **A5** 到 **D8**\)。  
  
6.  在 \[選取資料來源\] 對話方塊中，按一下 \[確定\]。  
  
##  <a name="runtimedoclevel"></a> 在執行階段將圖表控制項加入文件層級專案  
 您可以在執行階段，以動態方式加入 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項。  當文件關閉時，動態建立的圖表便不再是文件中的主控制項。  如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### 以程式設計方式將圖表主控制項加入工作表  
  
1.  在 `Sheet1` 的 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> 事件處理常式中插入下列程式碼，以加入 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項。  
  
     [!code-csharp[Trin_VstcoreHostControlsExcel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/CS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreHostControlsExcel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreHostControlsExcel/VB/Sheet1.vb#1)]  
  
##  <a name="runtimeaddin"></a> 在執行階段於 VSTO 增益集專案中加入圖表控制項  
 您可以利用程式設計方式，在 VSTO 增益集專案中，將 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項加入任何開啟中的工作表。  如需詳細資訊，請參閱[在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)。  
  
 當工作表關閉時，動態建立的圖表控制項便不再是工作表中的主控制項。  如需詳細資訊，請參閱[在執行階段將控制項加入至 Office 文件](../vsto/adding-controls-to-office-documents-at-run-time.md)。  
  
#### 以程式設計方式將圖表控制項加入工作表  
  
1.  下列程式碼會產生開啟中之工作表的主項目，然後新增 <xref:Microsoft.Office.Tools.Excel.Chart> 控制項。  
  
     [!code-csharp[Trin_Excel_Dynamic_Controls#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/CS/ThisAddIn.cs#9)]
     [!code-vb[Trin_Excel_Dynamic_Controls#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Excel_Dynamic_Controls/VB/ThisAddIn.vb#9)]  
  
## 編譯程式碼  
 此範例需要：  
  
-   要繪製成圖表的資料，即工作表中 A5 到 D8 之間的範圍。  
  
## 請參閱  
 [在 VSTO 增益集的執行階段中擴充 Word 文件和 Excel 活頁簿](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Office 文件上的控制項](../vsto/controls-on-office-documents.md)   
 [圖表控制項](../vsto/chart-control.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  