---
title: "文字範本的安全性 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文字範本, 安全性"
ms.assetid: 567a2383-7d43-4acc-af4a-cd70b7a0151e
caps.latest.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 23
---
# 文字範本的安全性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文字範本有下列安全性考量：  
  
-   文字範本容易受到任意程式碼插入的攻擊。  
  
-   如果主應用程式用來尋找指示詞處理器的機制沒有安全保護，就有可能會讓惡意的指示詞處理器執行。  
  
## 任意程式碼  
 當您撰寫範本時，可以將任何程式碼放置在 \<\# \#\> 標記內。  如此便會允許從文字範本之內執行任意程式碼。  
  
 請確定您取得來自信任來源的範本，  而且務必警告應用程式的使用者，不要執行不是來自於信任來源的範本。  
  
## 惡意指示詞處理器  
 文字範本引擎會和轉換主應用程式以及一個或多個指示詞處理器互動，將範本文字轉換為輸出檔。  如需詳細資訊，請參閱[文字範本轉換流程](../modeling/the-text-template-transformation-process.md)。  
  
 如果主應用程式用來尋找指示詞處理器的機制沒有安全保護，就會有執行惡意指示詞處理器的風險。  惡意指示詞處理器可能會在範本執行時提供以 `FullTrust` 模式執行的程式碼。  如果您建立自訂文字範本轉換主應用程式，就必須使用安全保護機制 \(例如登錄\)，讓引擎可以找到指示詞處理器。