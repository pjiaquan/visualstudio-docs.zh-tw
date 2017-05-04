---
title: "如何：將 XMLMappedRange 控制項加入至工作表 | Microsoft Docs"
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
  - "控制項 [Visual Studio 中的 Office 程式開發], 加入至工作表"
  - "XMLMappedRange 控制項, 加入至工作表"
ms.assetid: e1d4f2a8-1157-49c2-9158-a1253b709cb8
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：將 XMLMappedRange 控制項加入至工作表
  將 XML 項目對應至 Microsoft Office Excel 中的儲存格時，Visual Studio 會自動將 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項加入至工作表。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項在 \[**工具箱**\] 或 \[**資料來源**\] 視窗中無法使用。  另外，您無法以程式的方式建立 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制項。  
  
### 若要將 XMLMappedRange 控制項加入工作表  
  
1.  在 Visual Studio 設計工具中開啟 Excel 活頁簿。  
  
2.  開啟要在其中加入控制項的工作表。  
  
3.  按一下 \[**開發人員**\] 索引標籤上的 \[**來源**\]。  
  
    > [!NOTE]  
    >  如果在 \[功能區\] 上看不到 \[**開發人員**\] 索引標籤，則必須先行啟用。  如需詳細資訊，請參閱[如何：在功能區顯示開發人員索引標籤](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
     \[**XML 原始檔**\] 工作窗格隨即出現。  
  
4.  在 \[**XML 原始檔**\] 工作窗格中按一下 \[**XML 對應**\]。  
  
5.  在 \[**XML 對應**\] 對話方塊中按一下 \[**加入**\]。  
  
     會出現 \[**XML 原始檔**\] 對話方塊。  
  
6.  從 \[**XML 原始檔**\] 對話方塊中選取 XML 結構描述，並按一下 \[**開啟**\]。  
  
     該結構描述會加入 \[**XML 對應**\] 對話方塊。  
  
7.  在 \[**XML 對應**\] 對話方塊中按一下 \[**確定**\]。  
  
8.  將項目從 \[**XML 原始檔**\] 工作窗格拖曳至工作表上的儲存格。  
  
     會建立 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange>，並將其加入專案。  
  
    > [!NOTE]  
    >  如果拖曳 \[**XML 原始檔**\] 工作窗格的父項目，則會建立 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制項。  
  
## 請參閱  
 [XmlMappedRange 控制項](../vsto/xmlmappedrange-control.md)   
 [使用擴充物件自動化 Excel](../vsto/automating-excel-by-using-extended-objects.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [如何：在 Visual Studio 內將結構描述對應至工作表](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  