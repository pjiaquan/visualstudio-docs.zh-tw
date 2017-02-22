---
title: "CvInitProvider 函式 | Microsoft Docs"
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
  - "cvmarkers/CvInitProvider"
helpviewer_keywords: 
  - "CvInitProvider 方法"
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvInitProvider 函式
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

初始化符號提供者。  必須在任何其他並行視覺化檢視SDK 函式之前呼叫。  
  
## 語法  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### 參數  
 `pGuid`  
 提供者 GUID。  不可為 NULL 。  
  
 `ppProvider`  
 要儲存提供者內容輸出變數的位址。  不可為 NULL 。  
  
## 傳回值  
 S\_OK，當提供者已成功初始化或以防萬一有任何錯誤的錯誤碼。  使用 SUCCEEDED\/FAILED 巨集來檢查錯誤條件。  
  
## 需求  
 **標題:** cvmarkers.h  
  
## 請參閱  
 [C\+\+ 程式庫參考](../profiling/cpp-library-reference.md)