---
title: "如何：以程式設計方式從 Outlook 電子郵件項目儲存附件 | Microsoft Docs"
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
  - "Outlook [Visual Studio 中的 Office 程式開發]，附件"
  - "電子郵件 [Visual Studio 中的 Office 程式開發]，附件"
  - "儲存電子郵件附件"
  - "郵件項目 [Visual Studio 中的 Office 程式開發]，附件"
  - "附件 [Visual Studio 中的 Office 程式開發]"
ms.assetid: 2f05e2bb-ae4f-407c-a6da-a3b1a4c31ab3
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# 如何：以程式設計方式從 Outlook 電子郵件項目儲存附件
  這個範例會在收件匣中收到郵件時，將電子郵件附件儲存至指定的資料夾。  
  
> [!IMPORTANT]  
>  只有在您將名為 **TestFileSave** 的資料夾加入在 C 的根目錄時，這個範例才能運作。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 範例  
 [!code-csharp[Trin_OL_SaveAttachments#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_SaveAttachments/CS/thisaddin.cs#1)]  
  
## 請參閱  
 [使用郵件項目](../vsto/working-with-mail-items.md)   
 [如何：以程式設計方式依名稱擷取資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)   
 [如何：以程式設計方式在特定資料夾中搜尋](../vsto/how-to-programmatically-search-within-a-specific-folder.md)  
  
  