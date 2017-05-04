---
title: "如何：以程式設計方式存取 Outlook 連絡人 | Microsoft Docs"
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
  - "連絡人 [Visual Studio 中的 Office 程式開發], 搜尋"
ms.assetid: ea2297ea-6802-40e4-af1a-1e511a71ec75
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何：以程式設計方式存取 Outlook 連絡人
  這個範例會找出姓氏含有指定之搜尋字串的所有連絡人。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 範例  
 [!code-csharp[Trin_OL_AccessContacts#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/CS/trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-csharp[Trin_OL_AccessContacts#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/CS/backup/trin_ol_accesscontacts/thisaddin.cs#1)]
 [!code-vb[Trin_OL_AccessContacts#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_OL_AccessContacts/VB/thisaddin.vb#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   在 \[**連絡人**\] 資料夾中，姓氏含有字串 "**Na"** \(例如 Tzipi Butnaru\) 的連絡人。  
  
## 請參閱  
 [使用連絡人項目](../vsto/working-with-contact-items.md)   
 [如何：以程式設計方式將項目加入至 Outlook 連絡人](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)   
 [如何：以程式設計方式搜尋特定的連絡人](../vsto/how-to-programmatically-search-for-a-specific-contact.md)   
 [如何：以程式設計方式在連絡人中搜尋電子郵件地址](../vsto/how-to-programmatically-search-for-an-e-mail-address-in-contacts.md)   
 [如何：以程式設計方式刪除 Outlook 連絡人](../vsto/how-to-programmatically-delete-outlook-contacts.md)  
  
  