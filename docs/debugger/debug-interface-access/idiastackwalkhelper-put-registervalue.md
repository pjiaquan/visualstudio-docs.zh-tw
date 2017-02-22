---
title: "IDiaStackWalkHelper::put_registerValue | Microsoft Docs"
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
  - "IDiaStackWalkHelper2::put_registerValue 方法"
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaStackWalkHelper::put_registerValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

設定暫存器的值。  
  
## 語法  
  
```cpp#  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### 參數  
 `index`  
 \[in\]介於[CV\_HREG\_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)列舉型別，指定要寫入的暫存器。  
  
 `NewVal`  
 \[in\]新的暫存器值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 值的大小，不論實作應該只將暫存器通常保存儲存的。  例如，8 位元暫存器會保留只有最低 8 位元的指定值。  
  
## 請參閱  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [CV\_HREG\_e 列舉](../../debugger/debug-interface-access/cv-hreg-e.md)