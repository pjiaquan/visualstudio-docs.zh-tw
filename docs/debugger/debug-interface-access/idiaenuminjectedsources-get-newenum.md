---
title: "IDiaEnumInjectedSources::get__NewEnum | Microsoft Docs"
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
  - "IDiaEnumInjectedSources::get__NewEnum 方法"
ms.assetid: f56cdcdb-dc71-43c7-82fe-e2500986f5bc
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumInjectedSources::get__NewEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>版的這個列舉值。  
  
## 語法  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### 參數  
 pRetVal  
 \[retval\] out傳回`IUnknown`代表的<xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT>版的這個列舉值。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 請參閱  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)