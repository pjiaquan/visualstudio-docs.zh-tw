---
title: "如何：以不執行程式碼的方式開啟 Office 方案"
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
  - "組件 [Visual Studio 中的 Office 程式開發], 略過"
  - "略過組件"
  - "文件 [Visual Studio 中的 Office 程式開發], 開啟但不執行程式碼"
  - "Office 文件 [Visual Studio 中的 Office 程式開發], 開啟但不執行程式碼"
  - "Office 方案 [Visual Studio 中的 Office 程式開發], 開啟"
  - "開啟 Office 方案"
  - "方案 [Visual Studio 中的 Office 程式開發], 開啟"
ms.assetid: a853d91c-9fd6-421a-b3a2-956b6b494b96
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# 如何：以不執行程式碼的方式開啟 Office 方案
  即使在使用者的 Office 應用程式中將 \[安全性\] 設定為 \[高\]，使用 Managed 程式碼擴充建立的 Microsoft Office 方案仍然會執行。  這是因為 .NET 組件程式碼安全性是由 Microsoft .NET Framework 管理，而非由 Microsoft Office 管理。  
  
 但是，您有時候會想開啟文件，卻不執行程式碼。  例如，在文件開啟時執行的程式碼可能會改變內容，但是您要在程式碼進行變更以前，先更新文件的外觀。  或者是，您可能要傳送附特定資訊的文件給某人，而不要讓程式碼執行，免得內容遭到變更。  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 有幾種方式可以開啟含有 Managed 程式碼擴充的文件或活頁簿，而不執行組件程式碼。  
  
### 若要使用 SHIFT 鍵略過組件  
  
-   按住 SHIFT，同時從 \[**檔案**\] 功能表開啟文件和活頁簿，以防止 Word 和 Excel 在文件開啟時引發初始設定事件。  
  
    > [!NOTE]  
    >  如果從 \[**快速入門**\] 工作窗格開啟文件或活頁簿，則按住 SHIFT 不能略過程式碼。  而且，按住 SHIFT 也不能防止文件開啟後引發事件。  
  
     如果您要開啟文件進行變更，而不想讓程式碼先執行而變更了文件，這個方法很有用。  
  
### 若要透過重新命名或移除略過組件  
  
-   如果擁有組件所在電腦的必要使用權限，可以重新命名或移除組件，讓文件或活頁簿找不到它。  這樣會造成每次開啟 Office 文件都引發錯誤。  
  
     如果有多人使用同一個方案，這個方法可以防止所有人執行方案。  如果程式碼或參考的伺服器中發現問題，而您要阻止所有使用者執行方案，這個方法很有用。  
  
## 請參閱  
 [保護 Office 方案](../vsto/securing-office-solutions.md)   
 [部署 Office 方案](../vsto/deploying-an-office-solution.md)   
 [設計和建立 Office 方案](../vsto/designing-and-creating-office-solutions.md)   
 [Office 方案中的應用程式和部署資訊清單](../vsto/application-and-deployment-manifests-in-office-solutions.md)  
  
  