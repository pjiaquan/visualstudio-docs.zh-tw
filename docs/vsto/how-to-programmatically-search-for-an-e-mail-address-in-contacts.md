---
title: "如何：以程式設計方式在連絡人中搜尋電子郵件地址"
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
  - "電子郵件 [Visual Studio 中的 Office 程式開發]，搜尋"
  - "連絡人 [Visual Studio 中的 Office 程式開發]，搜尋"
  - "搜尋連絡人"
ms.assetid: e973a407-8b94-45c7-acdf-fe330115fb33
caps.latest.revision: 25
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# 如何：以程式設計方式在連絡人中搜尋電子郵件地址
  本範例會在 \[連絡人\] 資料夾中，搜尋其電子郵件地址中有網域名稱 **example.com** 的連絡人。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 範例  
 [!code-csharp[Trin_OL_SearchEmail#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_SearchEmail/CS/thisaddin.cs#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   其電子郵件地址中有網域名稱 **example.com** \(例如 `somebody@example.com`\)，並具有名字和姓氏的連絡人。  
  
## 請參閱  
 [使用連絡人項目](../vsto/working-with-contact-items.md)   
 [如何：以程式設計方式傳送電子郵件](../vsto/how-to-programmatically-send-e-mail-programmatically.md)   
 [如何：以程式設計方式存取 Outlook 連絡人](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [如何：以程式設計方式將項目加入至 Outlook 連絡人](../vsto/how-to-programmatically-add-an-entry-to-outlook-contacts.md)  
  
  