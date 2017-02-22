---
title: "IDiaSession::findInlineFramesByVA | Microsoft Docs"
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
ms.assetid: df9e68f6-e0a4-4cf6-b11d-61c40351e0cd
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineFramesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取可讓用戶端透過所有在指定的相對虛擬位址\(RVA\) \(VA\)內嵌框架逐一查看的列舉值。  
  
## 語法  
  
```cpp#  
HRESULT findInlineFramesByVA (   
   IDiaSymbol*       parent,  
   ULONGLONG         va,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### 參數  
 `parent`  
 \[in\] 表示之父代的 `IDiaSymbol` 物件。  
  
 `va`  
 \[in\] 指定電子郵件地址做為VA。  
  
 `ppResult`  
 \[out\] 物件所包含的清單中擷取的 `IDiaEnumSymbols` 物件。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`，否則傳回錯誤碼。  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)