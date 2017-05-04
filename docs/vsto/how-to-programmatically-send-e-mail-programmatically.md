---
title: "如何：以程式設計方式傳送電子郵件 | Microsoft Docs"
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
  - "電子郵件 [Visual Studio 中的 Office 程式開發], 傳送"
  - "郵件項目 [Visual Studio 中的 Office 程式開發], 傳送電子郵件"
  - "Outlook [Visual Studio 中的 Office 程式開發], 建立電子郵件"
  - "Outlook [Visual Studio 中的 Office 程式開發], 傳送電子郵件"
ms.assetid: 4fa0e1b5-2caf-4a11-8626-df643b23f5f0
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：以程式設計方式傳送電子郵件
  這個範例會將電子郵件訊息傳送至電子郵件地址中含有網域名稱 **example.com** 的連絡人。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 範例  
 [!code-csharp[Trin_OL_ProgramEmail#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_ProgramEMail/CS/thisaddin.cs#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   電子郵件地址中含有網域名稱 **example.com** 的連絡人。  
  
## 穩固程式設計  
 請勿移除搜尋網域名稱 **example.com** 的篩選程式碼。  如果您移除該篩選條件，您的方案就會將電子郵件訊息傳送給所有連絡人。  
  
## 請參閱  
 [使用郵件項目](../vsto/working-with-mail-items.md)   
 [如何：以程式設計方式建立電子郵件項目](../vsto/how-to-programmatically-create-an-e-mail-item.md)   
 [如何：以程式設計方式存取 Outlook 連絡人](../vsto/how-to-programmatically-access-outlook-contacts.md)   
 [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  