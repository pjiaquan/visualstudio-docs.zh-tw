---
title: "IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaReadExeAtRVACallback::ReadExecutableAtRVA 方法"
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

讀取指定的起始於指定的相對虛擬位址 \(RVA\) 可執行檔中的位元組數。  
  
## 語法  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### 參數  
 `relativeVirtualAddress`  
 \[in\]若要開始讀取 RVA 的可執行檔中。  
  
 `cbData`  
 \[in\]若要讀取的位元組數目。  
  
 `pcbData`  
 \[\] out傳回讀取的位元組數目。  
  
 `data[]`  
 輸入 \[、 輸出\]會被填入從檔案讀取的位元組陣列。  
  
## 備註  
 這個方法會呼叫 DIA 支援程式碼中使用相對虛擬位址的可執行檔載入資料的位元組。  呼叫這個方法支援的[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)方法。  
  
## 請參閱  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)