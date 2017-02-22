---
title: "CvWriteAlert 函式 | Microsoft Docs"
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
  - "cvmarkers/CvWriteAlertVA"
  - "cvmarkers/CvWriteAlertVW"
  - "cvmarkers/CvWriteAlertA"
  - "cvmarkers/CvWriteAlertW"
helpviewer_keywords: 
  - "CvWriteAlertVW 方法"
  - "CvWriteAlertA 方法"
  - "CvWriteAlertVA 方法"
  - "CvWriteAlertW 方法"
ms.assetid: 937aa9d6-278a-4df3-bef7-151441df16d5
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvWriteAlert 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

寫入並行視覺化檢視追蹤檔案的警示。  
  
## 語法  
  
```  
HRESULT CvWriteAlertW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteAlertVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteAlertVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### 參數  
 `argList`  
 引數清單。  
  
 `pMarkerSeries`  
 有效的符號系列內容。  不可為 NULL 。  
  
 `pMessage`  
 訊息的格式字串。  不可為 NULL 。  
  
## 傳回值  
 當訊息成功寫入時S\_OK。  錯誤碼，以防萬一有任何錯誤。  使用 SUCCEEDED\/FAILED 巨集來檢查錯誤條件。  
  
## 需求  
 **標題:** cvmarkers.h  
  
 **Unicode:** CvWriteAlertW， CvWriteAlertVW  
  
 **ANSI:** CvWriteAlertA， CvWriteAlertVA  
  
## 請參閱  
 [C\+\+ 程式庫參考](../profiling/cpp-library-reference.md)