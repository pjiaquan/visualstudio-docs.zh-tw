---
title: "T4 CleanUpBehavior 指示詞 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9e5a211f-a3bf-4229-bff0-7d2e45b71c64
caps.latest.revision: 2
caps.handback.revision: 2
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 CleanUpBehavior 指示詞
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要在處理文字範本後刪除 appDomain，請加入下列幾行：  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 文字範本是在與主機處理序不同的 appDomain 中處理。  大部分情況下，若已處理一個文字範本，則會再次使用 appdomain 處理下一個範本。  但是，如果指定 CleanupBehavior，則會刪除 appDomain，並且會在新的 appDomain 中處理下一個範本。  
  
 這會減緩文字處理的速度，不過，其有助於確保處置資源。  
  
 這個指示詞只能在 Visual Studio 主機中起作用。