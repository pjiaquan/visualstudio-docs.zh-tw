---
title: "IActiveScriptErrorDebug110::GetExceptionThrownKind | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptErrorDebug110::QueryIsFirstChance"
ms.assetid: ecc16e54-93e4-4322-ae13-afa7cd860032
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptErrorDebug110::GetExceptionThrownKind
傳回會指出擲回的例外狀況類型的值。  
  
> [!IMPORTANT]
>  [IActiveScriptErrorDebug110 介面](../../winscript/reference/iactivescripterrordebug110-interface.md) 是由 PDM 11.0 和更新版本所實作。  可在 activdbg100.h 中找到。  
  
## 語法  
  
```  
HRESULT GetExceptionThrownKind(  
   SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND*  pExceptionKind  
);  
```  
  
#### 參數  
 `pExceptionKind`  
 \[out\] 擲回的例外狀況類型 \(例如，第一個可能發生的例外狀況或未處理的例外狀況\)，是由 [SCRIPT\_ERROR\_DEBUG\_EXCEPTION\_THROWN\_KIND 列舉](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md) 列舉值所表示。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括 \(但不限於\) 下表中的這些值。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 請參閱  
 [IActiveScriptErrorDebug110 介面](../../winscript/reference/iactivescripterrordebug110-interface.md)