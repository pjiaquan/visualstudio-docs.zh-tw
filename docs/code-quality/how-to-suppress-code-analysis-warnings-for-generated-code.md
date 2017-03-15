---
title: "如何：隱藏所產生程式碼的程式碼分析警告 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3a96434e-d419-43a7-81ba-95cccac835b8
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 5
---
# 如何：隱藏所產生程式碼的程式碼分析警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Managed 程式碼編譯器 \(Compiler\) 通常會產生程式碼，可供您加入專案中以協助快速開發程式碼。  此外，開發人員通常也會使用協力廠商工具，幫助他們快速開發應用程式。  這些工具也會產生可加入專案中的程式碼。  
  
 您可能想查看程式碼分析在產生的程式碼中發現的規則違規。  不過，如果您無法檢視及維護包含違規的程式碼，可能就不想查看這些違規。  
  
 在專案的 \[程式碼分析\] 屬性頁中的 \[**隱藏所產生程式碼的結果**\] 核取方塊，可讓您選取是否要看到協力廠商工具所產生程式碼的程式碼分析警告。  
  
> [!NOTE]
>  表單和範本中出現錯誤和警告時，這個選項不會隱藏所產生程式碼的程式碼分析錯誤和警告。  您可以同時檢視及維護表單或範本的原始程式碼。  
  
### 若要隱藏專案中所產生程式碼的警告  
  
1.  在 \[方案總管\] 中，以滑鼠右鍵按一下專案，然後按一下 \[**屬性**\]。  
  
2.  按一下 \[**程式碼分析**\]。  
  
3.  選取 \[**隱藏所產生程式碼的結果**\] 核取方塊。