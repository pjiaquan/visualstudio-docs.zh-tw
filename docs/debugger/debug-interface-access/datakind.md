---
title: "DataKind | Microsoft Docs"
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
  - "DataKind 列舉"
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DataKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

表示特定範圍的資料值。  
  
## 語法  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## 項目  
 DataIsUnknown  
 無法判斷資料符號。  
  
 DataIsLocal  
 資料項目是區域變數。  
  
 DataIsStaticLocal  
 資料項目是靜態的區域變數。  
  
 DataIsParam  
 資料項目是型式參數。  
  
 DataIsObjectPtr  
 資料項目是物件指標 \(`this`\)。  
  
 DataIsFileStatic  
 資料的項目是具有檔案範圍變數。  
  
 DataIsGlobal  
 資料項目是全域變數。  
  
 DataIsMember  
 資料項目是物件的成員變數。  
  
 DataIsStaticMember  
 資料項目是類別的靜態變數。  
  
 DataIsConstant  
 資料項目是常數值。  
  
## 備註  
 這個列舉型別中的值所傳回的[IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)方法。  
  
## 需求  
 標頭: cvconst.h  
  
## 請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)