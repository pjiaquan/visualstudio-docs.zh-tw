---
title: "如何：設定程式碼剖析工具效能規則 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.ruleseditor"
ms.assetid: a148b468-b849-4858-880a-808a6b47e596
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何：設定程式碼剖析工具效能規則
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 程式碼剖析工具的效能警告指出應用程式中發生了問題，可能會降低程式執行速度。  警告也會指出，您可能需要變更收集方法，才能收集更有用的資料。  效能警告會自動在程式碼剖析工作階段中產生，並顯示於 **\[錯誤清單\]** 視窗中，當在[!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]整合式開發環境 \(IDE\) 中開啟程式碼剖析資料檔案時。  有些警告可能不適用您要查看的案例，有些警告則是誤報。  您可以設定效能警告來顯示或隱藏特定警告。  
  
### 若要設定分析工具效能警告  
  
1.  在 \[**工具**\] 功能表上，按一下 \[**選項**\]。  
  
2.  展開 \[**效能工具**\]，然後按一下 \[**規則**\]。  
  
3.  若要啟用或停用警告，請選取或清除警告 \[**識別碼**\] 和名稱旁的核取方塊。  
  
4.  若要指定規則的警告層級，請按一下規則旁邊的 \[**動作**\] 儲存格，然後按一下警告層級。  
  
    -   **停用**：停用規則 \(與清除規則 ID 旁邊的核取方塊效果相同\)。  
  
    -   **警告**：將規則顯示為警告。  
  
    -   **錯誤**：停止執行程式碼剖析，並將規則顯示為錯誤。  
  
    -   **資訊**：顯示此規則，僅供參考之用。