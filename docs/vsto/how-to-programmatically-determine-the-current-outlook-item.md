---
title: "如何：以程式設計方式判斷目前的 Outlook 項目"
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
  - "電子郵件 [Visual Studio 中的 Office 程式開發], 目前的項目"
  - "郵件項目 [Visual Studio 中的 Office 程式開發], 目前的"
  - "Outlook [Visual Studio 中的 Office 程式開發], 目前的項目"
  - "SelectionChange 事件"
ms.assetid: b4fb5ccd-b297-463e-9208-1fec42482531
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# 如何：以程式設計方式判斷目前的 Outlook 項目
  這個範例會使用 Explorer.SelectionChange 事件來顯示目前資料夾的名稱，以及已選取項目的某些相關資訊。  之後，程式碼就會顯示選取的項目。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 範例  
 [!code-csharp[Trin_OL_CurrentItem#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/CS/thisaddin.cs#1)]
 [!code-vb[Trin_OL_CurrentItem#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_CurrentItem/VB/thisaddin.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   Microsoft Office Outlook 中的約會、連絡人和電子郵件項目。  
  
## 請參閱  
 [Outlook 物件模型概觀](../vsto/outlook-object-model-overview.md)   
 [如何：以程式設計方式依名稱擷取資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何：以程式設計方式搜尋特定的連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)  
  
  