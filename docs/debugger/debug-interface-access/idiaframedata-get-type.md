---
title: "IDiaFrameData::get_type | Microsoft Docs"
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
  - "IDiaFrameData::get_type 方法"
ms.assetid: efca38b5-c479-4d0a-a164-f903f25c5509
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaFrameData::get_type
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取編緝器特定的框架類型。  
  
## 語法  
  
```cpp#  
HRESULT get_type (   
   DWORD* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回值，從[StackFrameTypeEnum 列舉](../../debugger/debug-interface-access/stackframetypeenum.md)指示編緝器特定的框架類型的列舉型別。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [StackFrameTypeEnum 列舉](../../debugger/debug-interface-access/stackframetypeenum.md)