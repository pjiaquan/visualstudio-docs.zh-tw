---
title: "IDiaSymbol::get_isSafeBuffers | Microsoft Docs"
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
  - "IDiaSymbol::get_isSafeBuffers 方法"
ms.assetid: f29e373d-e7bb-4181-ab9f-bf708d401d83
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_isSafeBuffers
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指定是否使用安全的緩衝區的 preprocesser 指示詞。  何時使用[SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)設定為 \[ `SymTagFunction`。  
  
## 語法  
  
```cpp#  
HRESULT get_isSafeBuffers(   
   BOOL* pRetVal)  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回`TRUE`如果指標為安全的緩衝區 ； 使用前置處理器指示詞 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 備註  
  
## 需求  
 標頭: Dia2.h  
  
 媒體櫃： diaguids.lib  
  
 DLL： msdia100.dll  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [strict\_gs\_check](/visual-cpp/preprocessor/strict-gs-check)