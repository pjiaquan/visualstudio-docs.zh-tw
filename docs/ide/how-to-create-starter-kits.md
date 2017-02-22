---
title: "如何：建立入門套件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "入門套件, 建立"
ms.assetid: ed7d1844-7c01-424a-a831-5003efe0f7bc
caps.latest.revision: 22
caps.handback.revision: 22
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：建立入門套件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

入門套件包含完整應用程式的程式碼，以及說明如何修改或擴充應用程式的文件。  建立入門套件基本上和建立一般專案範本的方式相同，唯一的差異處在於入門套件包含文件檔，這些文件檔設定為當根據入門套件建立專案時開啟。  
  
## 設計和開發入門套件  
 首先，您必須識別要開發之入門套件的類型，並且定義目標使用者。  然後，設計專案和文件，使其符合您的目標。  
  
 如果您是建立範例應用程式或外掛程式：  
  
-   建立一個建置無誤的專案。  
  
-   加入樣板程式碼，以便實作其他工作 \(選擇性\)。  
  
-   準備文件。  
  
 如果您是建立學習工具：  
  
-   建立一個建置無誤的專案。  
  
-   組織資源，例如程式碼片段和項目範本。  
  
-   準備文件。  
  
## 建立範本  
 在您完成了專案和文件之後，即可建立入門套件的專案範本。  這個程序和建立專案範本完全相同。  
  
 下列各主題包含建立範本的相關資訊。  
  
 [如何：建立專案範本](../ide/how-to-create-project-templates.md)  
 解說如何使用 \[**匯出範本**\] 精靈建立範本。  
  
 [如何：更新現有的範本](../ide/how-to-update-existing-templates.md)  
 說明如何編輯匯出的範本。  請使用這個程序修改 .vstemplate 檔，以自訂您的入門套件。  
  
## 請參閱  
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [自訂範本](../ide/customizing-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)