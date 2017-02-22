---
title: "IDiaTable::get__NewEnum | Microsoft Docs"
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
  - "IDiaTable::get__NewEnum 方法"
ms.assetid: ee89bba8-5d5c-4a0b-aa0d-1aad56baa380
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaTable::get__NewEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>版的這個列舉值。  
  
## 語法  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### 參數  
 `pRetVal`  
 \[\] out傳回`IUnknown`代表的<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>版的這個列舉值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)