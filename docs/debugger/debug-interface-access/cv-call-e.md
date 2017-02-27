---
title: "CV_call_e | Microsoft Docs"
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
  - "CV_call_e 列舉"
ms.assetid: f230560b-4243-432d-8f19-46df112043b9
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# CV_call_e
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

指定之函式的呼叫慣例。  
  
> [!NOTE]
>  只有最常見的列舉值都會在此說明。  Cvconst.h 標頭檔中有完整的列舉型別。  
  
## 語法  
  
```cpp#  
typedef enum CV_call_e {   
   CV_CALL_NEAR_C    = 0x00,  
   CV_CALL_NEAR_FAST = 0x04,  
   CV_CALL_NEAR_STD  = 0x07,  
   CV_CALL_NEAR_SYS  = 0x09,  
   CV_CALL_THISCALL  = 0x0b,  
   CV_CALL_CLRCALL   = 0x16  
} CV_call_e;  
```  
  
## 項目  
 CV\_CALL\_NEAR\_C  
 指定使用近處的從右至左推入函式呼叫慣例。  呼叫的函式會清除堆疊。  
  
 CV\_CALL\_NEAR\_FAST  
 指定暫存器中使用近處左\-右推入函式呼叫慣例。  呼叫的函式會使用參數的位元組總數，以清除堆疊。  
  
 CV\_CALL\_NEAR\_STD  
 指定函式呼叫慣例使用近處標準的呼叫 \(由右至左推入型\)。  
  
 CV\_CALL\_NEAR\_SYS  
 指定使用近端系統呼叫的函式呼叫慣例。  
  
 CV\_CALL\_THISCALL  
 指定函式呼叫慣例，使用`this`呼叫 \(`this`暫存器中傳遞的指標\)。  
  
 CV\_CALL\_CLRCALL  
 指定使用由通用語言執行階段 \(CLR\) \(也就是 managed 程式碼呼叫慣例\) 函式呼叫慣例。  
  
## 備註  
 這個列舉型別中的值會傳回由呼叫[IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)方法。  
  
## 需求  
 標頭: cvconst.h  
  
## 請參閱  
 [列舉和結構](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)