---
title: "IDiaFrameData::get_lengthParams | Microsoft Docs"
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
  - "IDiaFrameData::get_lengthParams 方法"
ms.assetid: a9177ed6-9ba8-4384-b411-24cad07d031b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_lengthParams
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取的推入堆疊的參數的位元組數目。  
  
## 語法  
  
```cpp#  
HRESULT get_lengthParams (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回的參數的位元組數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 備註  
 這個方法所傳回的值通常用於程式字串的解譯方式 \(請參閱[IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)程式字串的定義的方法\)。  
  
## 請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)