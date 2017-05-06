---
title: "如何：將 XMLNodes 控制項加入至 Word 文件"
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
  - "控制項 [Visual Studio 中的 Office 程式開發], 加入至文件"
  - "XMLNodes 控制項, 加入至文件"
ms.assetid: 315c6def-51f6-4ba6-bd9e-55cdf70f15bf
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 如何：將 XMLNodes 控制項加入至 Word 文件
  在**重要** 有關 Microsoft Word 的本主題開頭的資訊位於美國境外及其疆土或者使用對個人的優點和使用完整呈現和組織，或者執行中開發程式，由在選取範圍從之前的 Microsoft 授權之 Microsoft Word 產品，，當 Microsoft 從 Microsoft Word 移除特定功能的實作與自訂 XML 相關。  這些有關 Microsoft Word 的資訊不得供位於美國或其行政區以內，使用 Microsoft 在 2010 年 1 月 10 日以後所授權之 Microsoft Word 產品或開發適用程式之個人或組織閱讀或使用。凡是在該日期以前授權或是針對在美國地區以外使用所購買並授權的這些產品，其行為將有所不同。  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 當您將重複的 XML 結構描述項目對應至 Microsoft Office Word 文件時，Visual Studio 會自動將 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項加入至文件。  
  
 如需對應非重複 XML 結構描述項目的詳細資訊，請參閱 [如何：將 XMLNode 控制項加入至 Word 文件](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)。  
  
> [!NOTE]  
>  您無法從 \[**工具箱**\] 或 \[**資料來源**\] 視窗使用 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項，也不能以程式設計的方式建立此控制項。  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### 若要將 XMLNodes 控制項加入至文件  
  
1.  在 Visual Studio 設計工具的文件中，按一下功能區上的 \[**開發人員**\] 索引標籤。  
  
    > [!NOTE]  
    >  如果 \[**開發人員**\] 索引標籤沒有顯示，您必須先使其顯示。  如需詳細資訊，請參閱[如何：在功能區顯示開發人員索引標籤](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)。  
  
2.  按一下 \[**XML**\] 群組中的 \[**結構描述**\]。  
  
     \[**範本與增益集**\] 對話方塊隨即開啟。  
  
3.  按一下 \[**XML 結構描述**\] 索引標籤。  
  
4.  按一下 \[**加入結構描述**\]。  
  
     \[**加入結構描述**\] 對話方塊隨即開啟。  
  
5.  選取包含重複結構描述項目的 XML 結構描述，然後按一下 \[**開啟**\]。  
  
     \[**結構描述設定**\] 對話方塊便會出現。  
  
6.  指派別名，或按一下 \[**確定**\] 以加入結構描述而不指派別名。  
  
     該結構描述會加入至 \[**加入結構描述**\] 對話方塊。  
  
7.  在 \[**加入結構描述**\] 對話方塊中按一下 \[**確定**\]。  
  
     \[**XML 結構**\] 工作窗格隨即開啟。  
  
8.  在 \[**XML 結構**\] 工作窗格中按一下重複的結構描述項目，將它加入至文件。  
  
     如此便會建立 <xref:Microsoft.Office.Tools.Word.XMLNodes> 控制項並將它加入至專案。  
  
## 請參閱  
 [XMLNodes 控制項](../vsto/xmlnodes-control.md)   
 [使用擴充物件自動化 Word](../vsto/automating-word-by-using-extended-objects.md)   
 [主項目和主控制項概觀](../vsto/host-items-and-host-controls-overview.md)   
 [主項目和主控制項的程式設計限制](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  