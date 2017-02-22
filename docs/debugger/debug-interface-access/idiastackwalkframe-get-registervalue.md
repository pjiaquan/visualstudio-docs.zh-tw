---
title: "IDiaStackWalkFrame::get_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkFrame::get_registerValue 方法"
ms.assetid: ca3c20a9-934a-4b2c-a7f6-7d06e8611ff2
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkFrame::get_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取暫存器的值。  
  
## 語法  
  
```cpp#  
HRESULT get_registerValue (   
   DWORD      index,  
   ULONGLONG* pRetVal  
);  
```  
  
#### 參數  
 `index`  
 \[in\]介於[CV\_HREG\_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)指定的暫存器，要取得其值為列舉型別。  
  
 `pRetVal`  
 \[\] out傳回目前的暫存器值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [CV\_HREG\_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)