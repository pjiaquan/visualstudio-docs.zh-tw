---
title: "IDiaSegment::get_execute | Microsoft Docs"
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
  - "IDiaSegment::get_execute 方法"
ms.assetid: 746cdf8e-9097-415d-ba10-069854153185
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSegment::get_execute
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指出是否可執行檔的區段。  
  
## 語法  
  
```cpp#  
HRESULT get_execute (   
   BOOL* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回`TRUE`如果區段標示為可執行檔。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果這個屬性不受支援。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)