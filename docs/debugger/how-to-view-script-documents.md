---
title: "如何：檢視指令碼文件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "指令碼總管"
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 22
caps.handback.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：檢視指令碼文件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在舊版的 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中，從伺服器端指令碼產生的用戶端指令碼檔會出現在 \[指令碼總管\] 視窗中。  \[指令碼總管\] 視窗通常會隱藏起來，因此用戶端指令碼的存在不一定那麼明顯。  
  
 在 [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] 中，從伺服器端指令碼產生的用戶端指令碼檔會出現在 \[指令碼總管\] 視窗中，而 \[方案總管\] 預設為可見狀態。  今後將不再有 \[指令碼總管\] 視窗。  
  
 只有在您處於偵錯模式或中斷模式時，才會看得見用戶端指令碼檔。  這些檔案會出現在 \[**指令碼文件**\] 節點中。  
  
 伺服器端指令碼檔一律可見。  這些檔案會出現在 \[**\<網站路徑名稱\>**\] 節點中。  該節點的名稱與此範例類似：`c:\...\Website2\`  
  
### 若要檢視伺服器端指令碼文件  
  
1.  在 \[**方案總管**\] 中，開啟 \[**\<網站路徑名稱\>**\] 節點。  
  
2.  按兩下您想要檢視的指令碼檔。  
  
     伺服器端指令碼檔會在來源視窗中開啟。  
  
### 若要檢視用戶端指令碼文件  
  
1.  在 \[**方案總管**\] 中，開啟 \[**指令碼文件**\] 節點。  
  
2.  按兩下您想要檢視的指令碼檔。  
  
     用戶端指令碼檔會在來源視窗中開啟。  
  
## 請參閱  
 [在偵錯工具中檢視資料](../debugger/viewing-data-in-the-debugger.md)