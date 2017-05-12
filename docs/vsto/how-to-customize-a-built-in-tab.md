---
title: "如何：自訂內建索引標籤"
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
  - "內建索引標籤 [Visual Studio 中的 Office 程式開發]"
  - "功能區 [Visual Studio 中的 Office 程式開發], 索引標籤"
ms.assetid: 197a7aaa-a51d-496c-b904-b9421849fad9
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 如何：自訂內建索引標籤
  您可在內建索引標籤加入群組和控制項。  內建索引標籤是已位在 Microsoft Office 應用程式功能區的索引標籤。  例如，\[資料\] 索引標籤就是 Excel 的內建索引標籤。  當您建立自訂群組時，它會出現在索引標籤的最末端，但是您可以在索引標籤上任意移動群組。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
> [!NOTE]  
>  您可以在內建索引標籤加入群組，但無法從內建索引標籤移除內建群組。  
  
### 在內建索引標籤加入群組  
  
1.  以滑鼠右鍵按一下 \[方案總管\] 中的功能區程式碼檔，然後按一下 \[檢視設計工具\]。  
  
    > [!NOTE]  
    >  如果 \[方案總管\] 中未出現功能區程式碼檔，即必須在您的專案中加入 \[功能區項目\]。  請參閱[如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  請以滑鼠右鍵按一下功能區設計工具中的任何索引標籤，然後按一下 \[屬性\]。  
  
3.  在 \[屬性\] 視窗中展開 \[ControlId\] 屬性，然後將 \[ControlIdType\] 屬性設為 \[Office\]。  
  
4.  將 \[OfficeId\] 屬性設為您想自訂的內建索引標籤*「控制項 ID」*\(control ID\)。  
  
     控制項 ID 是唯一識別 Microsoft Office 應用程式內建索引標籤、群組和控制項的名稱。  
  
     如需控制項 ID 的清單，請參閱 [Office 2010 說明檔：Office Fluent 使用者介面控制項識別碼](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
5.  從 \[工具箱\] 的 \[Office 功能區控制項\] 索引標籤，將群組拖曳至索引標籤。  
  
    > [!NOTE]  
    >  內建群組不會顯示在設計工具中。  因此，判斷所用是否為內建索引標籤的唯一方法，是檢查索引標籤的 \[ControlId\] 屬性。  
  
### 將群組放置在內建索引標籤  
  
1.  在功能區設計工具中，選取自訂群組。  
  
2.  在 \[屬性\] 視窗中，展開 \[Position\] 屬性。  
  
3.  將 \[PositionType\] 屬性設為適當的值：  
  
    -   \[BeforeOfficeId\] 會將群組放置在指定的內建群組之前。  
  
    -   \[AfterOfficeId\] 會將群組放置在指定的內建群組之後。  
  
4.  將 \[OfficeId\] 屬性設為內建群組的控制項 ID。  
  
     如需控制項 ID 的清單，請參閱 [Office 2010 說明檔：Office Fluent 使用者介面控制項識別碼](http://go.microsoft.com/fwlink/?LinkID=181052)。  
  
## 請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [逐步解說：使用功能區 XML 建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)   
 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [如何：變更功能區索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  