---
title: "IDiaTable::Item | Microsoft Docs"
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
  - "IDiaTable::Item 方法"
ms.assetid: eae11b26-4807-400c-be25-e85bbc0c6b20
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaTable::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取指定的項目，在資料表中的參考。  
  
## 語法  
  
```cpp#  
HRESULT Item (   
   DWORD      index,  
   IUnknown** element  
);  
```  
  
#### 參數  
 `index`  
 \[in\]索引的資料表中的項目範圍從 0 到`count`\-1，其中`count`傳回的[IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)方法。  
  
 `element`  
 \[\] out傳回`IUnknown`物件，代表指定的表格項目。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 資料表代表物件的集合。  這些物件中，根據項目參數就可以轉換成適當的介面。  例如，如果資料表含有[IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)物件，然後將項目參數就可以轉換成`IDiaSegment`介面。  
  
 它是較常見的方法，呼叫`QueryInterface`中的方法[IDiaTable](../../debugger/debug-interface-access/idiatable.md)為適當的列舉值介面的介面，並使用列舉值的特定方法來存取目錄。  請參閱[IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)介面的範例。  
  
## 請參閱  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaTable::get\_Count](../../debugger/debug-interface-access/idiatable-get-count.md)   
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)   
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)