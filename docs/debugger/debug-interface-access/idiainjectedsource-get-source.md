---
title: "IDiaInjectedSource::get_source | Microsoft Docs"
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
  - "IDiaInjectedSource::get_source 方法"
ms.assetid: 3c0b5386-321f-4f8f-85cc-e2ee7b4cc3d2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaInjectedSource::get_source
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取來源的程式碼位元組。  
  
## 語法  
  
```cpp#  
HRESULT get_source (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### 參數  
 `cbData`  
 \[in\]代表資料的緩衝區大小的位元組數目。  
  
 `pcbData`  
 \[\] out傳回的位元組數目，表示的位元組傳回。  如果`data`是`NULL`，然後`pcbData`為止的總位元組數的資料。  
  
 `data[]`  
 \[\] out要填入的來源位元組的緩衝區。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)