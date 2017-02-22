---
title: "CvLeaveSpan 函式 | Microsoft Docs"
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
  - "cvmarkers/CvLeaveSpan"
helpviewer_keywords: 
  - "CvLeaveSpan 方法"
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvLeaveSpan 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

標記延伸的結尾。  
  
## 語法  
  
```  
HRESULT CvLeaveSpan(  
   _In_ PCV_SPAN pSpan  
);  
```  
  
#### 參數  
 `pSpan`  
 展開先前呼叫方法所傳回的物件CvEnterSpan\*。  不可為 NULL 。  
  
## 傳回值  
 S\_OK，當訊息成功寫入。  錯誤碼，以防萬一有任何錯誤。  使用 SUCCEEDED\/FAILED 巨集來檢查錯誤條件。  
  
## 需求  
 **標題:** cvmarkers.h  
  
## 請參閱  
 [C\+\+ 程式庫參考](../profiling/cpp-library-reference.md)