---
title: "IDiaEnumSymbolsByAddr::symbolByAddr | Microsoft Docs"
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
  - "IDiaEnumSymbolsByAddr::symbolByAddr 方法"
ms.assetid: 0b6f5a68-8402-4f29-8219-20576fda8166
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumSymbolsByAddr::symbolByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

將列舉值置於藉由執行對應的影像區段編號\] 與 \[位移。  
  
## 語法  
  
```cpp#  
HRESULT symbolByAddr (   
   DWORD**      isect,  
   DWORD**      offsect,  
   IDiaSymbol** ppsymbol  
);  
```  
  
#### 參數  
 isect  
 \[in\]影像區段編號。  
  
 offsect  
 \[in\]這個範例一節中。  
  
 ppsymbol  
 \[\] out傳回[IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)物件，代表找到該符號。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`如果找不到符號。  否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)