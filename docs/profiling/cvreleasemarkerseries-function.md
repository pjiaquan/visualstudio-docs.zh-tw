---
title: "CvReleaseMarkerSeries 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvReleaseMarkerSeries"
helpviewer_keywords: 
  - "CvReleaseMarkerSeries 方法"
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvReleaseMarkerSeries 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

釋放標記系列。  請勿在原本發行應用程式之後使用簽章，否則系列物件可能會損毀。  無法釋放標記系列造成記憶體遺漏 \(Memory Leak\)。  
  
## 語法  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### 參數  
 `pMarkerSeries`  
 提供者物件變數位址。  位址不能為 null，變數可以有任何值。  
  
## 傳回值  
 S\_OK，當一系列標記已成功建立或以防萬一有任何錯誤碼錯誤。   使用 SUCCEEDED\/FAILED 巨集來檢查錯誤條件。  
  
## 需求  
 **標題:** cvmarkers.h  
  
## 請參閱  
 [C\+\+ 程式庫參考](../profiling/cpp-library-reference.md)