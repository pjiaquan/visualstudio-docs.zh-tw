---
title: "如何：以程式設計方式使網頁與 Outlook 資料夾產生關聯 | Microsoft Docs"
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
  - "資料夾 [Visual Studio 中的 Office 程式開發], Web 網頁和"
  - "Outlook [Visual Studio 中的 Office 程式開發], 附加至資料夾的 Web 網頁"
  - "Web 網頁 [Visual Studio 中的 Office 程式開發], Outlook 資料夾"
ms.assetid: b211b1b2-11e4-4316-87b7-98a3d10f95d1
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 16
---
# 如何：以程式設計方式使網頁與 Outlook 資料夾產生關聯
  這個範例會檢查 Microsoft Office Outlook 中名為 `HtmlView` 的資料夾是否存在。  如果此資料夾不存在，程式碼就會建立此資料夾並指派 Web 網頁給它。  如果此資料夾存在，則程式碼就會顯示資料夾內容。  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## 範例  
 [!code-csharp[Trin_OL_HTMLFolder#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_OL_HTMLFolder/CS/thisaddin.cs#1)]  
  
## 請參閱  
 [使用資料夾](../vsto/working-with-folders.md)   
 [如何：以程式設計方式依名稱擷取資料夾](../vsto/how-to-programmatically-retrieve-a-folder-by-name.md)   
 [如何：以程式設計方式建立自訂資料夾項目](../vsto/how-to-programmatically-create-custom-folder-items.md)  
  
  