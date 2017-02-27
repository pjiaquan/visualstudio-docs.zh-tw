---
title: "BasicType | Microsoft Docs"
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
  - "BasicType 列舉"
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# BasicType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定符號的基本型別。  
  
## 語法  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## 項目  
 btNoType  
 未不指定任何基本的類型。  
  
 btVoid  
 基本的型別是`void`。  
  
 btChar  
 基本的型別是`char` \(C\/C\+\+ 型別\)。  
  
 btWChar  
 基本的型別是否為寬 \(Unicode\) 字元 \(`WCHAR`\)。  
  
 btInt  
 基本的型別是`signed int` \(C\/C\+\+ 型別\)。  
  
 btUInt  
 基本的型別是`unsigned int` \(C\/C\+\+ 型別\)。  
  
 btFloat  
 基本的型別是浮點數 \(`FLOAT`\)。  
  
 btBCD  
 基本的型別是二進位編碼小數 \(`BCD`\)。  
  
 btBool  
 基本的型別是布林值 \(`BOOL`\)。  
  
 btLong  
 基本的型別是`long int` \(C\/C\+\+ 型別\)。  
  
 btULong  
 基本的型別是`unsigned long int` \(C\/C\+\+ 型別\)。  
  
 btCurrency  
 基本的型別是貨幣。  
  
 btDate  
 基本的型別是日期\/時間 \(`DATE`\)。  
  
 btVariant  
 基本的型別是一種變數型別結構 \(`VARIANT`\)。  
  
 btComplex  
 基本的型別是複合的數字。  
  
 btBit  
 基本的型別是陡峭。  
  
 btBSTR  
 基本的型別是基本或二進位字串 \(`BSTR`\)。  
  
 btHresult  
 基本的型別是`HRESULT`。  
  
## 備註  
 這個列舉型別中的值所傳回的[IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)方法。  
  
## 需求  
 標頭: cvconst.h  
  
## 請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)