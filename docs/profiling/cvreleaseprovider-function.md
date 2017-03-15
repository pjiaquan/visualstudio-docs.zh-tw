---
title: "CvReleaseProvider 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvReleaseProvider"
helpviewer_keywords: 
  - "CvReleaseProvider 方法"
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvReleaseProvider 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

釋放標記提供者。  釋放標記提供者並不會影響這個提供者先前建立的標記系列。  標記數列必須分別由 CvReleaseMarkerSeries 呼叫釋放。  無法釋放提供者會造成記憶體遺漏 \(Memory Leak\)。  
  
## 語法  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### 參數  
 `pProvider`  
 提供者內容。  不可為 NULL 。  
  
## 傳回值  
 S\_OK，當成功釋放提供者或有任何錯誤時顯示錯誤碼。  使用 SUCCEEDED\/FAILED 巨集來檢查錯誤條件。  
  
## 需求  
 **標題:** cvmarkers.h  
  
## 請參閱  
 [C\+\+ 程式庫參考](../profiling/cpp-library-reference.md)