---
title: "如何：以程式設計方式在 Outlook 中移動項目 | Microsoft Docs"
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
  - "Outlook 資料夾 [Visual Studio 中的 Office 程式開發], 移動項目"
ms.assetid: ac524f2e-a3e8-496d-bd5a-714799be44ab
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# 如何：以程式設計方式在 Outlook 中移動項目
  這個範例會從 \[**收件匣**\] 將未讀取的電子郵件訊息移至名為 **Test** 的資料夾中。  此範例只會移動 `Subject` 欄位中含有 **Test** 文字的訊息。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 範例  
 [!code-csharp[Trin_OL_MoveItems#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_MoveItems/CS/thisaddin.cs#1)]  
  
## 編譯程式碼  
 這個範例需要：  
  
-   名為 **Test** 的 Outlook 郵件資料夾。  
  
-   送達時 `Subject` 欄位中含有 **Test** 文字的電子郵件訊息。  
  
## 請參閱  
 [使用資料夾](../vsto/working-with-folders.md)   
 [如何：以程式設計方式依名稱擷取資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何：以程式設計方式在特定資料夾中搜尋](../vsto/how-to-programmatically-search-within-a-specific-folder.md)   
 [如何：以程式設計方式在收到電子郵件訊息時執行動作](../vsto/how-to-programmatically-perform-actions-when-an-e-mail-message-is-received.md)  
  
  