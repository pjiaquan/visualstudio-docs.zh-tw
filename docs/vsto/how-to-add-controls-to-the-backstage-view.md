---
title: "如何：將控制項加入至 Backstage 檢視"
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
  - "控制項, 功能區"
  - "自訂功能區, 功能表"
  - "自訂功能區, 功能表"
  - "功能表, 自訂"
  - "Microsoft Office 按鈕"
  - "Microsoft Office 功能表"
  - "Office 按鈕"
  - "功能區, 自訂"
  - "功能區, 功能表"
ms.assetid: 4fda1278-9aea-4d54-928a-269a81584494
caps.latest.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 29
---
# 如何：將控制項加入至 Backstage 檢視
  您可以使用功能區設計工具將控制項加入至功能表，然後按一下 \[**檔案**\] 索引標籤。  當您執行應用程式時，您加入至 \[**檔案**\] 索引標籤顯示在控制項群組 \[**增益集**\]。  
  
 使用 Visual Studio 中，功能區設計工具不放在內建控制項之前或之後可以放置控制項。  一個內部控制項是已經出現在幕後檢視的控制項。  如果您想要將控制項放在內建控制項之前或之後，則必須使用功能區 XML。  如需 \[**功能區 \(XML\)**\] 的資訊，請參閱 [功能區 XML](../vsto/ribbon-xml.md)。  如需自訂幕後檢視的詳細資訊，請參閱[給開發人員的 Office 2010 幕後檢視簡介](http://go.microsoft.com/fwlink/?LinkId=182189) \(英文\) 和[針對開發人員自訂 Office 2010 幕後檢視](http://go.microsoft.com/fwlink/?LinkId=182188) \(英文\)。  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### 將控制項加入至幕後檢視  
  
1.  在設計檢視中開啟功能區項目。  
  
     如需如何將 \[**功能區 \(視覺化設計工具\)**\] 項目加入至專案的詳細資訊，請參閱 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)。  
  
2.  在功能區設計工具中，按一下 \[**檔案**\] 索引標籤。  
  
     功能表設計工具隨即出現。  這個設計介面不包含任何控制項。  
  
3.  從 \[**工具箱**\] 的 \[**Office 功能區控制項**\] 索引標籤將下列任何控制項拖曳到功能表設計工具上。  
  
    -   Button  
  
    -   CheckBox  
  
    -   Gallery  
  
    -   Menu  
  
    -   Separator  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  拖曳控制項，將其移到功能表上的新位置。  
  
## 請參閱  
 [功能區概觀](../vsto/ribbon-overview.md)   
 [功能區設計工具](../vsto/ribbon-designer.md)   
 [功能區 XML](../vsto/ribbon-xml.md)   
 [如何：開始自訂功能區](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [逐步解說：使用功能區設計工具建立自訂的索引標籤](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  