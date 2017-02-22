---
title: "IDiaLoadCallback::RestrictSymbolServerAccess | Microsoft Docs"
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
  - "IDiaLoadCallback::RestrictSymbolServerAccess 方法"
ms.assetid: db37ad9f-f75e-4f0c-83bf-21a6e66ba859
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaLoadCallback::RestrictSymbolServerAccess
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

決定是否允許對存取符號伺服器來解析符號。  
  
## 語法  
  
```cpp#  
HRESULT RestrictSymbolServerAccess();  
```  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回錯誤碼。  
  
## 備註  
 任何傳回碼，而非`S_OK`可防止使用符號伺服器來解析符號。  
  
## 請參閱  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)