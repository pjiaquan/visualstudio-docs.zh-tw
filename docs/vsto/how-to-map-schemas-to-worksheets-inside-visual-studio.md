---
title: "如何：在 Visual Studio 內將結構描述對應至工作表"
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
  - "Excel [Visual Studio 中的 Office 程式開發], XML 結構描述"
  - "對應 [Visual Studio 中的 Office 程式開發], XML 結構描述至 Excel 工作表"
  - "工作表 [Visual Studio 中的 Office 程式開發], XML 結構描述"
  - "XML 結構描述 [Visual Studio 中的 Office 程式開發], 對應"
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# 如何：在 Visual Studio 內將結構描述對應至工作表
  在 Visual Studio 中開啟工作表時，可以將 XML 結構描述對應至該工作表。  您所使用的 Microsoft Office Excel 工具與在 Visual Studio 外部開啟活頁簿時使用的工具相同。  無論您是在建立 Excel 方案之前還是之後將結構描述對應至工作表，Office 專案都會建立相同的物件。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  您不能在 Excel 方案中使用多重 XML 結構描述。  
  
### 若要在 Visual Studio 中將 XML 結構描述對應至 Excel 工作表  
  
1.  在 Visual Studio 內開啟 Excel 活頁簿或範本專案。  
  
2.  在工作表中按一下，以將焦點移至設計工具。  
  
3.  按一下 \[功能區\] 上的 \[**開發人員**\] 索引標籤。  
  
    > [!NOTE]  
    >  如果 \[**開發人員**\] 索引標籤沒有顯示，您必須先使其顯示。  如需詳細資訊，請參閱[如何：在功能區顯示開發人員索引標籤](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
4.  按一下 \[**XML**\] 群組中的 \[**來源**\]。  
  
     \[**XML 原始檔**\] 視窗隨即開啟。  
  
5.  按一下 \[**XML 原始檔**\] 視窗中的 \[**XML 對應**\]。  
  
     \[**XML 對應**\] 對話方塊隨即開啟。  
  
6.  在 \[**XML 對應**\] 對話方塊中按一下 \[**加入**\]。  
  
7.  瀏覽至結構描述檔案，選取它並按一下 \[**開啟**\]。  
  
8.  按一下 \[**確定**\]。  
  
     結構描述會顯示在 \[**XML 原始檔**\] 視窗中。  在專案中，會根據結構描述產生具型別的 <xref:System.Data.DataSet>，並建立 <xref:System.Windows.Forms.BindingSource>。  
  
9. 拖曳 \[**XML 原始檔**\] 視窗中項目，將其放置在工作表中要建立對應控制項的位置。  
  
     如果拖曳非重複的結構描述項目， Office 專案會產生自動繫結至 <xref:System.Windows.Forms.BindingSource>的 <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> 控制。  
  
     如果您將一個重複的結構描述項目， Office 專案產生沒有自動繫結至資料來源的 <xref:Microsoft.Office.Tools.Excel.ListObject> 控制。  如需詳細資訊，請參閱[文件層級自訂中的 XML 結構描述和資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)。  
  
## 請參閱  
 [如何：在 Visual Studio 內將結構描述對應至 Word 文件](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [文件層級自訂中的 XML 結構描述和資料](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  