---
title: "如何：設定 Office 方案的組態資訊 | Microsoft Docs"
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
  - "組態檔 [Visual Studio 中的 Office 程式開發]"
  - "方案 [Visual Studio 中的 Office 程式開發], 組態檔"
ms.assetid: f123838f-957a-4cf5-acc0-0cc0f4c2aea2
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# 如何：設定 Office 方案的組態資訊
  您可以使用組態檔，設定 Office 方案特有的設定。  您可以指定的設定包括：組件繫結原則、遠端物件、偵錯和追蹤設定。  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
### 若要將組態檔加入至 Office 專案中  
  
1.  在 \[**專案**\] 功能表上，按一下 \[**加入新項目**\]。  
  
2.  按一下 \[**分類**\] 窗格中的 \[**一般**\]。  
  
3.  選取 \[**範本**\] 窗格中的 \[**應用程式組態檔**\]。  
  
4.  在 \[**名稱**\] 方塊中，輸入與組件 \(Assembly\) 相同的名稱，並加上副檔名 .config。  例如，名為 ExcelWorkbook1.dll 之 Excel 專案組件的組態檔就會名為 ExcelWorkbook1.dll.config。  
  
5.  按一下 \[**加入**\]。  
  
6.  根據應用程式組態檔描述結構建立組態檔。  如需詳細資訊，請參閱[.NET Framework 的組態檔結構描述](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)。  
  
 在 Office 專案中使用組態檔並沒有任何特殊考量。  
  
## 請參閱  
 [.NET Framework 的組態檔結構描述](http://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)  
  
  