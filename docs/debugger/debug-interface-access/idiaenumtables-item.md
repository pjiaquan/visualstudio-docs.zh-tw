---
title: "IDiaEnumTables::Item | Microsoft Docs"
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
  - "IDiaEnumTables::Item 方法"
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取資料表的索引或名稱。  
  
## 語法  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### 參數  
 `index`  
 \[in\]索引或名稱的[IDiaTable](../../debugger/debug-interface-access/idiatable.md)而無法擷取。  如果使用整數變數，則它必須是介於 0 到`count`\-1，其中`count`時傳回的[IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)方法。  
  
 `table`  
 \[\] out傳回[IDiaTable](../../debugger/debug-interface-access/idiatable.md)物件，代表您想要的資料表。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 如果指定字串變數，則字串命名特定的資料表。  如所述，名稱應該是其中一個資料表名稱[常數 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)。  
  
## 範例  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## 請參閱  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [常數 \(偵錯介面存取 SDK\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)