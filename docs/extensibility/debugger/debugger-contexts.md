---
title: "偵錯工具內容 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "偵錯的 [偵錯 SDK]，內容"
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 偵錯工具內容
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]可偵錯時，偵錯引擎 \(DE\) 操作同時在數個不同的內容，，如下所示：  
  
-   程式碼的內容，其中描述該應用程式的執行資料流中目前的位置。  
  
-   文件內容的位置，也將告訴您來源文件中目前的位置。  
  
-   運算式評估內容，將告訴您哪一個運算式中評估就會啟動的內容。  
  
## 本章節內容  
 [程式碼內容](../../extensibility/debugger/code-context.md)  
 在今天的執行階段架構與非語言中，其中的程式碼可能無法顯示的指示，但其他方法的程式的指令資料流中的地址作為討論的程式碼的內容。  
  
 [文件位置](../../extensibility/debugger/document-position.md)  
 定義在 Visual Studio 的偵錯的原始程式檔視為已知 ide 中的某個位置的抽象概念中的文件位置。  
  
 [文件內容](../../extensibility/debugger/document-context.md)  
 將告訴您哪些文件內容表示相對於原始程式檔的 Visual Studio 偵錯。  也將告訴您如何符號處理常式對應至文件內容的程式碼的內容。  
  
 [運算式評估內容](../../extensibility/debugger/expression-evaluation-context.md)  
 提供在 Visual Studio 中，運算式評估內容的相關資訊。  比方說，堆疊框架相關聯，運算式評估內容提供的內容來評估區域變數、 方法參數和類別成員。  
  
## 相關章節  
 [偵錯概念](../../extensibility/debugger/debugger-concepts.md)  
 描述主要的偵錯架構概念。  
  
 [偵錯元件](../../extensibility/debugger/debugger-components.md)  
 提供 Visual Studio 的偵錯元件，包括偵錯引擎 \(DE\)、 運算式評估工具 \(EE\)，以及符號處理常式 \(SH\) 的概觀。  
  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)  
 包含各種偵錯工作的詳細資訊，例如啟動的程式，並評估運算式的連結。