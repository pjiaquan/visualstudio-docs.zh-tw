---
title: "如何：在偵錯時切換到另一個執行緒 | Microsoft Docs"
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
  - "執行緒, 切換 [偵錯]"
ms.assetid: 5cd76c52-76fa-4fcc-b37e-e9f0ecac0e9e
caps.latest.revision: 26
caps.handback.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# 如何：在偵錯時切換到另一個執行緒
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

當您偵錯多執行緒應用程式時，您可以使用數個方法中的任何一種方法，將內容從目前使用的執行緒切換至另一個執行緒。  
  
### 切換至執行緒視窗中出現的任何執行緒  
  
-   按兩下執行緒。  
  
### 若要切換至來源視窗中的執行緒  
  
-   在左側裝訂邊，以滑鼠右鍵按一下執行緒指標，再指向 \[**切換至**\]，然後按一下您要做為切換目標之執行緒的名稱。  捷徑功能表只會顯示該特定位置上的執行緒。  
  
     如果沒有指標出現，請以滑鼠右鍵按一下 \[**執行緒**\] 視窗，並確認已選取 \[**在原始程式檔中顯示執行緒**\]。  
  
### 若要切換至偵錯位置工具列中的執行緒  
  
1.  按一下 \[**偵錯位置**\] 工具列上的 \[**執行緒**\] 方塊。  
  
2.  在清單中，按一下您要切換至哪個執行緒。  
  
## 請參閱  
 [偵錯多執行緒應用程式](../debugger/debug-multithreaded-applications-in-visual-studio.md)