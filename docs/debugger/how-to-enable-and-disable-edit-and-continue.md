---
title: "如何：啟用和停用編輯後繼續 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "/INCREMENTAL 連結器選項"
  - "套用程式碼變更命令"
  - "中斷模式, 套用程式碼變更"
  - "程式碼變更, 在中斷模式套用"
  - "編輯後繼續, 套用程式碼變更"
  - "編輯後繼續, 停用"
  - "編輯後繼續, 啟用"
  - "Go 命令"
  - "INCREMENTAL 連結器選項"
  - "Step 命令"
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：啟用和停用編輯後繼續
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以在設計階段於 \[**選項**\] 對話方塊中停用或啟用 \[編輯後繼續\]。  但是在進行偵錯時，無法變更這項設定。  
  
 \[編輯後繼續\] 只能用於偵錯組建中。  在原生 C\+\+ 中，\[編輯後繼續\] 必須使用 \/INCREMENTAL 選項。  
  
## 程序  
  
#### 若要啟用\/停用編輯後繼續  
  
1.  在 \[**工具**\] 功能表上，按一下 \[**選項**\]。  
  
2.  在 \[**選項**\] 對話方塊中，開啟 \[**偵錯**\] 節點，然後選取 \[**編輯後繼續**\] 分類。  
  
3.  若要啟用，請選取 \[**啟用編輯後繼續**\] 核取方塊。  若要停用，請清除該核取方塊。  
  
    > [!NOTE]
    >  如果已啟用 IntelliTrace，而且您同時收集 IntelliTrace 事件和呼叫資訊，則會停用 \[編輯後繼續\]。  如需詳細資訊，請參閱[設定 IntelliTrace 以收集偵錯資訊](http://msdn.microsoft.com/zh-tw/7657ecab-e07e-4b1b-872d-f05d966be37e)。  
  
4.  按一下 \[**確定**\]。  
  
## 請參閱  
 [編輯後繼續](../debugger/edit-and-continue.md)   
 [選項對話方塊、偵錯、編輯後繼續](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)