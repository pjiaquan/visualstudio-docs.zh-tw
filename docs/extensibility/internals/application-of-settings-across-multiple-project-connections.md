---
title: "跨多個專案的連接設定的應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "原始檔控制外掛程式，應用程式的設定"
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 跨多個專案的連接設定的應用程式
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

使用原始檔控制外掛程式 API 1.2，建置可以跨越多個專案或多個連線內容中執行相同的原始檔控制作業批次作業使用的原始檔控制外掛程式。  批次可用來消除重複、 每個專案的使用者經驗的對話方塊。  
  
 如果使用者選取多個隸屬於多個連線中的原始檔控制外掛程式使用原始檔控制外掛程式 API 1.1 \(的例如，兩個 Web 專案在不同的檔案共用的電腦上\) 建置的項目，並檢查它們，使用者看到重複出現的對話方塊。  即使在使用者按一下就會這樣**套用至所有**因為 IDE 會重設其狀態，以每個連線內容\] 核取方塊\] 對話方塊中的。  
  
## 新功能的旗標  
 `SccBeginBatch`函式集`SCC_CAP_BATCH`旗標，表示批次作業正在進行中  
  
## 新函式  
 下列的新功能支援批次作業：  
  
-   [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
-   [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
 `SCCBeginBatch`函式會啟動一群原始檔控制作業。  `SccEndBatch`關閉群組。  可能不是巢狀群組。  
  
## 請參閱  
 [原始檔控制外掛程式 API 版本 1.2 新功能](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)