---
title: "如何：將功能區設計工具的功能區匯出到功能區 XML | Microsoft Docs"
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
  - "自訂功能區, XML"
  - "自訂功能區, XML"
  - "匯出功能區"
  - "功能區 [Visual Studio 中的 Office 程式開發], 匯出"
  - "功能區 [Visual Studio 中的 Office 程式開發], XML"
  - "功能區設計工具 [Visual Studio 中的 Office 程式開發]"
  - "XML [Visual Studio 中的 Office 程式開發], 功能區"
ms.assetid: 96e0e9ed-4392-4f45-ac33-b6f7c22ea321
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 如何：將功能區設計工具的功能區匯出到功能區 XML
  \[**功能區 \(視覺化設計工具\)**\] 項目不支援所有可能的功能區自訂類型。  若要以進階的方式自訂功能區，您可以從設計工具將功能區匯出至功能區 XML，並且直接編輯 XML。  
  
> [!NOTE]  
>  並非所有屬性值都會出現在功能區 XML 檔中。  如需詳細資訊，請參閱[功能區概觀](../vsto/ribbon-overview.md)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### 將功能區設計工具的功能區匯出到功能區 XML  
  
1.  以滑鼠右鍵按一下 \[**方案總管**\] 中的功能區程式碼檔，然後按一下 \[**設計工具檢視**\]。  
  
2.  以滑鼠右鍵按一下功能區設計工具，然後按一下 \[**將功能區匯出至 XML**\]。  
  
     Visual Studio 會將功能區 XML 檔案和功能區 XML 程式碼檔加入至專案。  
  
3.  在功能區程式碼類別中，尋找開頭為 `TODO:.` 的註解。  
  
4.  根據您開發的方案類型而定，將這些註解中的程式碼區塊複製到 \[**ThisAddin**\]、\[**ThisWorkbook**\] 或 \[**ThisDocument**\] 類別中。  
  
     此程式碼可以讓 Microsoft Office 應用程式探索及載入您的自訂功能區。  如需詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
5.  在 \[**ThisAddin**\]、\[**ThisWorkbook**\] 或 \[**ThisDocument**\] 類別中，取消程式碼區塊的註解。  
  
     取消註解程式碼之後，程式碼應該類似下列範例。  在這個範例中，功能區類別稱為 `MyRibbon`。  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  切換到功能區 XML 程式碼檔案並尋找 `Ribbon Callbacks` 區域。  
  
     這是您撰寫回呼方法以處理使用者動作 \(例如按一下按鈕\) 的區域。  
  
7.  針對您在功能區設計工具程式碼中撰寫的每個事件處理常式建立回呼方法。  
  
8.  將您所有的事件處理常式程式碼從事件處理常式移到回呼方法，並且修改程式碼以便配合功能區擴充性 \(RibbonX\) 程式設計模型使用。  
  
     如需撰寫回呼方法及使用 RibbonX 程式設計模型的詳細資訊，請參閱[功能區 XML](../vsto/ribbon-xml.md)。  
  
## 請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [逐步解說：使用功能區 XML 建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  