---
title: "CV_access_e | Microsoft Docs"
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
helpviewer_keywords: 
  - "CV_access_e 列舉"
ms.assetid: 33c05d65-abb4-4800-a382-54a3805ea7b0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# CV_access_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定的成員函式和變數的可視性 \(存取層級\) 的範圍。  
  
## 語法  
  
```cpp#  
typedef enum CV_access_e {   
   CV_private   = 1,  
   CV_protected = 2,  
   CV_public    = 3  
} CV_access_e;  
```  
  
## 項目  
 CV\_private  
 成員具有私用存取。  
  
 CV\_protected  
 成員有保護的存取權。  
  
 CV\_public  
 成員都有公用存取。  
  
## 備註  
 `friend`存取規範不包含此處，因為它通常會使用類別的私用和受保護的項目存取的非成員函式。  使用[IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)方法，以尋找符號與`SymTagFriend`的存取。  
  
## 需求  
 標頭: cvconst.h  
  
## 請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)   
 [IDiaSymbol::get\_symTag](../Topic/IDiaSymbol::get_symTag.md)