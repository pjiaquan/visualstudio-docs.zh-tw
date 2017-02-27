---
title: "IDiaSession::findInlineFramesByRVA | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: ddb3ff0e-cb3d-4fa0-af56-f064b218b264
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineFramesByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取可讓用戶端透過所有在指定的相對虛擬位址\(RVA\) \(RVA\)內嵌框架逐一查看的列舉值。  
  
## 語法  
  
```cpp#  
HRESULT findInlineFramesByRVA (   
   IDiaSymbol*       parent,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### 參數  
 `parent`  
 \[in\] 表示之父代的 `IDiaSymbol` 物件。  
  
 `rva`  
 \[in\] 指定電子郵件地址做為 RVA。  
  
 `ppResult`  
 \[out\] 物件所包含的清單中擷取的 `IDiaEnumSymbols` 物件。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`，否則傳回錯誤碼。  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)