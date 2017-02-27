---
title: "CvWriteFlag 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvWriteFlagExVA"
  - "cvmarkers/CvWriteFlagExW"
  - "cvmarkers/CvWriteFlagExVW"
  - "cvmarkers/CvWriteFlagExA"
helpviewer_keywords: 
  - "CvWriteFlagExW 方法"
  - "CvWriteFlagExVA 方法"
  - "CvWriteFlagExA 方法"
  - "CvWriteFlagExVW 方法"
ms.assetid: ee9da1e2-7b34-4cba-81e2-215d25d32e4d
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# CvWriteFlag 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

將旗標寫入至並行視覺化檢視追蹤檔案。  
  
## 語法  
  
```  
HRESULT CvWriteFlagExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteFlagExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### 參數  
 `argList`  
 引數清單。  
  
 `category`  
 分類  
  
 `level`  
 重要性。  
  
 `pMarkerSeries`  
 有效的符號系列內容。  不可為 NULL 。  
  
 `pMessage`  
 訊息的格式字串。  不可為 NULL 。  
  
## 傳回值  
 S\_OK，當訊息成功寫入。  錯誤碼，以防萬一有任何錯誤。  使用 SUCCEEDED\/FAILED 巨集來檢查錯誤條件。  
  
## 需求  
 **標題:** cvmarkers.h  
  
 **Unicode:** CvWriteFlagExW， CvWriteFlagExVW  
  
 **ANSI:**CvWriteFlagExA， CvWriteFlagExVA  
  
## 請參閱  
 [C\+\+ 程式庫參考](../profiling/cpp-library-reference.md)