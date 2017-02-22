---
title: "IDiaFrameData::get_lengthProlog | Microsoft Docs"
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
  - "IDiaFrameData::get_lengthProlog 方法"
ms.assetid: 5f042ff1-e74e-430a-be34-d2cf1b18eff2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_lengthProlog
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取初構中的程式碼區塊的位元組的數目。  
  
## 語法  
  
```cpp#  
HRESULT get_lengthProlog (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回的初構程式碼的位元組數目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 備註  
 初構程式碼是一系列指令，可保留登錄、 設定 CPU 狀態和建立堆疊的函式。  
  
## 請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)