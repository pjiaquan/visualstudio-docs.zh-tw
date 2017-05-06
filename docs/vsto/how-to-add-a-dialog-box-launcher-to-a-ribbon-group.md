---
title: "如何：在功能區群組中加入對話方塊啟動程式"
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
  - "對話方塊啟動器 [Visual Studio 中的 Office 程式開發]"
  - "功能區 [Visual Studio 中的 Office 程式開發], 對話方塊啟動器"
ms.assetid: 5972664f-4e37-4dc6-90d0-69cedd057e60
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# 如何：在功能區群組中加入對話方塊啟動程式
  您可以將對話方塊啟動程式加入至功能區上的任何群組。  對話方塊啟動程式是出現在群組中的小型圖示。  使用者按下這個圖示即可開啟相關的對話方塊或是工作窗格，其中提供更多與群組相關的選項。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### 在功能區群組中加入對話方塊啟動程式  
  
1.  在 \[**方案總管**\] 中選取功能區程式碼檔 \(.vb 或 .cs 檔\)。  
  
2.  在 \[**檢視**\] 功能表上，按一下 \[**設計工具**\]。  
  
3.  在功能區設計工具中，以滑鼠右鍵按一下任何群組，然後按一下 \[**加入 DialogBoxLauncher**\]。  
  
     將程式碼加入至群組的 <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> 事件，即可開啟自訂或內建對話方塊。  
  
## 請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [在執行階段存取功能區](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Office 程式開發範例和逐步解說](../vsto/office-development-samples-and-walkthroughs.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區物件模型概觀](../vsto/ribbon-object-model-overview.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [如何：將功能區設計工具的功能區匯出到功能區 XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [如何：變更功能區索引標籤的位置](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [如何：自訂內建索引標籤](../vsto/how-to-customize-a-built-in-tab.md)   
 [如何：將控制項加入至 Backstage 檢視](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [自訂 Outlook 的功能區](../vsto/customizing-a-ribbon-for-outlook.md)   
 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [如何：顯示增益集使用者介面錯誤](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [逐步解說：在執行階段更新功能區中的控制項](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [逐步解說：使用功能區 XML 建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  