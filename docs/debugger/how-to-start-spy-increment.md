---
title: "How to: Start Spy++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Spy++, starting"
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# How to: Start Spy++
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以從 Visual Studio 或在命令提示字元啟動 Spy\+\+。  
  
 啟動 Spy\+\+ 時，如果出現要求提供權限以變更電腦的訊息，請按一下 \[**是**\]。  
  
> [!NOTE]
>  您一次只能執行一個 Spy\+\+ 執行個體。  如果嘗試執行另一個執行個體，只會讓目前執行中的執行個體取得焦點。  
  
### 若要從 Visual Studio 啟動 Spy\+\+  
  
-   按一下 \[**工具**\] 功能表上的 \[**Spy\+\+**\]。  
  
     因為 Spy\+\+ 獨立執行，在啟動後就可以關閉 Visual Studio。  
  
    > [!NOTE]
    >  記錄 Spy\+\+ 的訊息時，可能會造成作業系統的執行速度緩慢。  
  
### 若要在命令提示字元啟動 Spy\+\+  
  
1.  在 \[命令提示字元\] 視窗中，將目錄變更為含有 spyxx.exe 的資料夾。  這個資料夾通常是 ..  \\*Visual Studio installation folder*\\Common7\\Tools\\。  
  
2.  輸入 **spyxx.exe**，然後按 ENTER。  
  
## 請參閱  
 [Using Spy\+\+](../debugger/using-spy-increment.md)   
 [Spy\+\+ Views](../debugger/spy-increment-views.md)   
 [Spy\+\+ Reference](../debugger/spy-increment-reference.md)