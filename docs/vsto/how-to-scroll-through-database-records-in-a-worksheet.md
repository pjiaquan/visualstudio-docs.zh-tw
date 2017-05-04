---
title: "如何：在工作表中捲動資料庫記錄 | Microsoft Docs"
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
  - "資料 [Visual Studio 中的 Office 程式開發], 捲動資料庫資料錄"
  - "資料庫 [Visual Studio 中的 Office 程式開發], 捲動資料錄"
  - "資料錄 [Visual Studio 中的 Office 程式開發], 捲動"
  - "工作表 [Visual Studio 中的 Office 程式開發], 捲動資料錄"
ms.assetid: aea4c86c-9d6d-47dd-8977-066e21945dab
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# 如何：在工作表中捲動資料庫記錄
  下列程序示範如何使用設計工具，在 Microsoft Office Excel 工作表中顯示資料庫資料表中的單一資料欄位，以及讓使用者可以捲動所有記錄的控制項。  
  
 您只能在文件層級專案中使用設計工具。  不過，您也可以在執行階段，透過程式設計的方式加入控制項並繫結至資料。  如需詳細資訊，請參閱[逐步解說：VSTO 增益集專案中的簡單資料繫結](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)。  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### 若要在工作表中捲動資料庫記錄  
  
1.  在 Visual Studio 中開啟 Excel 應用程式專案。  
  
2.  開啟 \[**資料來源**\] 視窗，並建立資料庫的資料來源。  如需詳細資訊，請參閱[如何：連接至資料庫中的資料](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md)。  
  
3.  展開包含您要顯示之資料的資料表，並選取特定的資料行。  
  
4.  開啟控制項清單，並選取 \[**NamedRange**\]。  
  
5.  將 <xref:Microsoft.Office.Tools.Excel.NamedRange> 控制項拖曳至要顯示資料的儲存格中。  
  
6.  從 \[**工具箱**\] 的 \[**Windows Form**\] 索引標籤，將 <xref:System.Windows.Forms.BindingNavigator> 控制項加入至工作表，並設定要使用的控制項。  如需詳細資訊，請參閱[BindingNavigator 控制項概觀 &#40;Windows Form&#41;](../Topic/BindingNavigator%20Control%20Overview%20(Windows%20Forms).md)。  
  
## 請參閱  
 [將資料繫結至 Office 方案中的控制項](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  