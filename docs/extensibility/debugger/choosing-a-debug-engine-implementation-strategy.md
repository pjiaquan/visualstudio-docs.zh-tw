---
title: "選擇偵錯引擎的實作策略 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯引擎，實作策略"
ms.assetid: 90458fdd-2d34-4f10-82dc-6d8f31b66d8b
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# 選擇偵錯引擎的實作策略
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用執行階段架構，以判斷您的偵錯引擎 \(DE\) 實作策略。  偵錯引擎可能會建立同處理序到程式偵錯，同處理序 Visual Studio 的工作階段偵錯管理員 \(SDM\)，或逾時\-跨處理序，這兩者。  下列方針應該可以幫助您從中選取下列三種策略。  
  
## 方針  
 雖然有可能是跨處理序 DE SDM 和程式以進行偵錯，就通常沒有必要這麼做。  跨處理序界限的呼叫會相當緩慢。  
  
 偵錯引擎早已經提供 Win32 原生執行階段環境，以及通用語言執行階段環境。  如果您必須取代 DE 任何這些環境中，您必須建立 SDM DE 同處理序。  
  
 否則，您可以選擇建立 DE，同處理序以 SDM 或同處理序偵錯的程式。  請務必考慮 DE 的運算式評估工具是否需要經常存取程式的符號存放區，以及是否能夠符號存放區載入至快速存取的記憶體。  也請考慮下列各項：  
  
-   如果並不會有許多符號存放區中，運算式評估工具之間的呼叫，或符號存放區可讀取的 SDM 記憶體空間，建立 DE 同處理序以 SDM。  其會連接到您的程式時您必須回到 SDM 的偵錯引擎的 CLSID。  SDM 會使用這個 CLSID 來建立同處理序的執行個體 DE。  
  
-   如果 DE 必須呼叫程式存取符號存放區，請與程式建立 DE 同處理序。  如此一來，程式會建立 DE 的執行個體。  
  
## 請參閱  
 [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)