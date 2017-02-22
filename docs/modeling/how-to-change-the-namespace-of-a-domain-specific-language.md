---
title: "如何：變更網域指定的語言命名空間 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "網域指定的語言, 命名空間"
ms.assetid: f20c47e5-230d-4f0e-812f-5c6edb86866c
caps.latest.revision: 19
caps.handback.revision: 19
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# 如何：變更網域指定的語言命名空間
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以變更為網域特定語言的命名空間。  您必須進行的變更 **DSL 總管**、 Dsl 封裝專案屬性，以及組件資訊。  
  
### 若要變更的網域特定語言的命名空間  
  
1.  在 **DSL 總管**，按一下 \[  **Dsl** 節點。  
  
2.  在**屬性** \] 視窗中，變更  **Namespace** 屬性。  
  
3.  儲存方案並轉換範本。  
  
4.  在**專案** \] 功能表中，按一下  **Dsl 屬性**。  
  
     為您的專案屬性會出現。  
  
5.  按一下 \[**應用程式**\] 索引標籤。  
  
6.  變更**預設命名空間**為新的命名空間名稱的屬性。  
  
7.  如果您還想要變更的組件名稱，變更**組件名稱屬性。**  
  
8.  如果您變更組件名稱，請開啟 DslPackage\\Package.tt，並更新這一行：  
  
     `string dslAssembly = "YourDSLassembly.Dsl.dll";`  
  
9. 如果您在撰寫任何自訂的程式碼，請確定要變更程式碼檔案中的命名空間和類別的參考。  
  
10. 重設 Visual Studio 實驗性的執行個體。  
  
    1.  刪除**\\Users\\***{name}***\\AppData\\Local\\Microsoft\\VisualStudio\\\*Exp**  
  
    2.  在 Windows 上**開始** \] 功能表中，選擇 **所有程式**，  **Visual Studio 2010 SDK Microsoft**， **工具**， **重設實驗性的執行個體**。  
  
11. 在**建置** \] 功能表中，選擇 **重建方案**。  
  
## 請參閱  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-tw/ca5e84cb-a315-465c-be24-76aa3df276aa)