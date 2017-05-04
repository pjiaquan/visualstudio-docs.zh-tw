---
title: "如何：防止 Outlook 顯示表單區域 | Microsoft Docs"
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
  - "取消表單區域顯示"
  - "表單區域 [Visual Studio 中的 Office 程式開發], 取消顯示"
ms.assetid: 82a25def-776a-476a-a72d-d0a48a827d3c
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：防止 Outlook 顯示表單區域
  在某些情況下，您可能不想讓 Microsoft Office Outlook 顯示特定項目的表單區域。  例如，連絡人項目未包含公司地址時，您便可以不讓地圖上標記公司位置的表單區域顯示。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
### 防止 Outlook 顯示表單區域  
  
1.  開啟要修改之表單區域的程式碼檔案。  
  
2.  展開 \[**表單區域 Factory**\] 程式碼區域。  
  
3.  將程式碼加入至 `FormRegionInitializing` 事件處理常式，以便將 <xref:Microsoft.Office.Tools.Outlook.FormRegionInitializingEventArgs> 類別的 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 屬性設為 **true**。  
  
 在這個範例中，如果連絡人項目未包含地址，則 <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> 屬性會設為 **true**，且表單區域就不會顯示。  
  
## 範例  
 [!code-csharp[Trin_Outlook_FR_Separate#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/CS/MapIt.cs#1)]
 [!code-vb[Trin_Outlook_FR_Separate#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Separate/VB/MapIt.vb#1)]  
  
## 請參閱  
 [建立 Outlook 表單區域](../vsto/creating-outlook-form-regions.md)   
 [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [如何：在 Outlook 增益集專案中加入表單區域](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [逐步解說：設計 Outlook 表單區域](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [逐步解說：匯入在 Outlook 中設計的表單區域](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)  
  
  