---
title: "CvIsEnabled 函式 | Microsoft Docs"
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
  - "cvmarkers/CvIsEnabledEx"
  - "cvmarkers/CvIsEnabled"
helpviewer_keywords: 
  - "CvIsEnabled 方法"
  - "CvIsEnabledEx 方法"
ms.assetid: 2e4fea6d-758d-4150-8744-6102a1d58c1c
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvIsEnabled 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

判斷是否有工作階段已啟用了標記 ETW 提供者。  
  
## 語法  
  
```  
HRESULT CvIsEnabled(  
   _In_ PCV_PROVIDER pProvider  
);  
HRESULT CvIsEnabledEx(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ CV_IMPORTANCE level,  
   _In_ int category  
);  
```  
  
#### 參數  
 `category`  
 分類  
  
 `level`  
 重要性。  
  
 `pProvider`  
 有效的提供者物件。  不可為 NULL 。  
  
## 傳回值  
 S\_OK，如果提供者目前為啟用狀態。  S\_FALSE，如果提供者目前已停用。  錯誤碼，以防萬一有任何錯誤。  使用失敗的巨集來檢查錯誤條件並檢查 S\_OK\/S\_FALSE。  
  
## 需求  
 **標題:** cvmarkers.h  
  
## 請參閱  
 [C\+\+ 程式庫參考](../profiling/cpp-library-reference.md)