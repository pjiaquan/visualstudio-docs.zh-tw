---
title: "如何：變更功能區索引標籤的位置"
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
  - "功能區 [Visual Studio 中的 Office 程式開發], 索引標籤"
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 25
---
# 如何：變更功能區索引標籤的位置
  您可以使用 \[**索引標籤集合編輯器**\] 變更功能區上自訂索引標籤的順序。  您可以將自訂索引標籤放置在功能區上的內建索引標籤前面或後面。  內建索引標籤是已在 Microsoft Office 應用程式功能區上的索引標籤。  例如，\[**資料**\] 索引標籤就是 Excel 的內建索引標籤。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### 變更功能區上索引標籤的順序  
  
1.  在 \[**方案總管**\] 中選取功能區程式碼檔 \(.vb 或 .cs 檔\)。  
  
2.  在 \[**檢視**\] 功能表上，按一下 \[**設計工具**\]。  
  
3.  以滑鼠右鍵按一下 \[功能區設計工具\]，然後按一下 \[**屬性**\]。  
  
4.  在 \[**屬性**\] 視窗中選取 \[**Tabs**\] 屬性，然後按一下省略符號按鈕 \(![ASP.NET Mobile 設計工具橢圓形](../sharepoint/media/mwellipsis.png "ASP.NET Mobile 設計工具橢圓形")\)。  
  
     \[**索引標籤集合編輯器**\] 隨即出現。  
  
5.  在 \[**索引標籤集合編輯器**\] 的 \[**成員**\] 清單中，選取要移動的索引標籤，然後按一下向上或向下箭頭改變索引標籤的順序。  
  
### 若要將索引標籤放置在功能區上的內建索引標籤前面或後面。  
  
1.  在 \[功能區設計工具\] 中，選取自訂索引標籤。  
  
2.  在 \[**屬性**\] 視窗，展開 \[**ControlId**\]屬性，然後確定 \[**ControlIdType**\]屬性的值設定為 \[**自訂**\]。  
  
3.  在 \[**屬性**\] 視窗中展開 \[**Position**\] 屬性。  
  
4.  將 \[**PositionType**\] 屬性設為適當的值：  
  
    -   \[**BeforeOfficeId**\] 會將群組放置在指定的內建索引標籤前面。  
  
    -   \[**AfterOfficeId**\] 會將群組放置在指定的內建索引標籤後面。  
  
5.  將 \[**OfficeId**\] 屬性設為內建索引標籤的控制項 ID。  
  
     如需控制項 ID 的清單，請參閱 [Microsoft 說明檔:Office Fluent 使用者介面控制項識別項](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
## 請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [逐步解說：使用功能區 XML 建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  