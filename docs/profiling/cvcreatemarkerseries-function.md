---
title: "CvCreateMarkerSeries 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvCreateMarkerSeriesA"
  - "cvmarkers/CvCreateMarkerSeriesW"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesA 方法"
  - "CvCreateMarkerSeriesW 方法"
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvCreateMarkerSeries 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

建立指定之提供者的正負號系列。  
  
## 語法  
  
```  
_Check_return_ HRESULT CvCreateMarkerSeriesW(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCWSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
  
_Check_return_ HRESULT CvCreateMarkerSeriesA(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
```  
  
#### 參數  
 `pProvider`  
 CvInitProvider 先前初始化之提供者的物件。  不可為 NULL 。  
  
 `pSeriesName`  
 標記的系列名稱。  不可以是 null，但允許空白字串。  
  
 `ppMarkerSeries`  
 要儲存的資料標記系列內容輸出變數的位址。  不可為 NULL 。  
  
## 傳回值  
 S\_OK，當一系列標記已成功建立或以防萬一有任何錯誤碼錯誤。  使用 SUCCEEDED\/FAILED 巨集來檢查錯誤條件。  
  
## 需求  
 **標題:** cvmarkers.h  
  
 **Unicode:** CvCreateMarkerSeriesW  
  
 **ANSI:** CvCreateMarkerSeriesA  
  
## 請參閱  
 [C\+\+ 程式庫參考](../profiling/cpp-library-reference.md)