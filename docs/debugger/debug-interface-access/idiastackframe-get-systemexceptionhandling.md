---
title: "IDiaStackFrame::get_systemExceptionHandling | Microsoft Docs"
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
  - "IDiaStackFrame::get_systemExceptionHandling"
ms.assetid: c76cf265-dea0-4159-883f-32b50bbef044
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackFrame::get_systemExceptionHandling
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

會擷取旗標，指出是否系統例外狀況處理將有效用。  
  
## 語法  
  
```cpp#  
HRESULT get_systemExceptionHandling (   
   BOOL* pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回`TRUE`如果系統例外狀況處理將有效用此框架中。 否則，會傳回`FALSE`。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。  傳回`S_FALSE`不支援的屬性。  否則，會傳回錯誤碼。  
  
## 備註  
 系統例外處理是也稱為結構化的例外處理。  這不是 C\+\+ 例外處理一樣。  
  
 若要判斷這是否作用中為 C\+\+ 例外處理，呼叫[IDiaStackFrame::get\_cplusplusExceptionHandling](../Topic/IDiaStackFrame::get_cplusplusExceptionHandling.md)方法。  
  
## 請參閱  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [IDiaStackFrame::get\_cplusplusExceptionHandling](../Topic/IDiaStackFrame::get_cplusplusExceptionHandling.md)