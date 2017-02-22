---
title: "IDiaSession::findInlineeLinesByVA | Microsoft Docs"
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
ms.assetid: dffe6594-e0d1-4ed5-aeea-8773f88d82a6
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineeLinesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取可讓用戶端透過指定的行號資訊逐一查看由指定之父代符號內嵌，直接或間接，以及在指定的相對虛擬位址 \(RVA\) \(VA\) 中的列舉型別。  
  
## 語法  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           parent,  
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### 參數  
 `parent`  
 \[in\] 表示之父代的 `IDiaSymbol` 物件。  
  
 `va`  
 \[in\] 指定電子郵件地址做為VA。  
  
 `length`  
 \[in\] 指定位址範圍，位元組數，而此查詢範圍。  
  
 `ppResult`  
 \[out\] 物件所包含資料列編號清單中擷取的 `IDiaEnumLineNumbers` 物件。  
  
## 傳回值  
 如果成功，則傳回 `S_OK`，否則傳回錯誤碼。  
  
## 請參閱  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum 列舉](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)