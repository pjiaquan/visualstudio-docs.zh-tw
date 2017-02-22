---
title: "CvCreateDefaultMarkerSeriesOfDefaultProvider 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider"
helpviewer_keywords: 
  - "CvCreateDefaultMarkerSeriesOfDefaultProvider 方法"
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvCreateDefaultMarkerSeriesOfDefaultProvider 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

建立預設的預設提供者的標記系列。  
  
## 語法  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### 參數  
 `ppProvider`  
 提供者物件變數位址。  位址不能為 null，變數可以有任何值。  
  
 `ppMarkerSeries`  
 標記位址系列物件變數。  位址不能為 null，變數可以有任何值。  
  
## 傳回值  
 S\_OK，當提供者和標記一系列已成功建立或錯誤碼，以防萬一有任何錯誤。  使用 SUCCEEDED\/FAILED 巨集來檢查錯誤條件。  
  
## 需求  
 **標題:** cvmarkers.h  
  
## 請參閱  
 [C\+\+ 程式庫參考](../profiling/cpp-library-reference.md)