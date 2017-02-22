---
title: "IDiaEnumFrameData::frameByRVA | Microsoft Docs"
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
  - "IDiaEnumFrameData::frameByRVA 方法"
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumFrameData::frameByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

傳回相對虛擬位址 \(RVA\) 的框架。  
  
## 語法  
  
```cpp#  
HRESULT frameByRVA(   
   DWORD           relativeVirtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### 參數  
 relativeVirtualAddress  
 \[in\]想要的框架陣列之 RVA。  
  
 框架  
 \[\] out傳回[IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)物件，代表含有圖文框，提供的地址。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果沒有框架資料符合指定的位址。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)