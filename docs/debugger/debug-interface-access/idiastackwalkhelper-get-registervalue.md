---
title: "IDiaStackWalkHelper::get_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::get_registerValue 方法"
ms.assetid: 46ac5eee-73a3-44a1-8635-6c58ba193cb6
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::get_registerValue
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
 \[in\]介於[CV\_HREG\_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)指定的登錄要從中取得值的列舉型別。  
  
 `pRetVal`  
 \[\] out傳回目前的暫存器值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 儘管大小的`pRetVal`參數，實作應該只將暫存器通常保存來儲存。  例如，8 位元暫存器會保留只有最低 8 位元的指定值。  8 位元值，此範圍將延伸，64 位元，從這個方法傳回時。  
  
## 請參閱  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV\_HREG\_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)