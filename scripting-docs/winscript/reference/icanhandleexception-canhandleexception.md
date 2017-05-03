---
title: "ICanHandleException::CanHandleException | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: ICanHandleException.CanHandleException
apilocation: scrobj.dll
helpviewer_keywords: 
  - "ICanHandleException::CanHandleException"
ms.assetid: 0fc703bf-9518-487e-af20-00e073b640f1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ICanHandleException::CanHandleException
判斷指令碼引擎的呼叫端是否可以處理指定的例外狀況。  
  
## 語法  
  
```  
HRESULT CanHandleException(  
   EXCEPINFO*  pExcepInfo,  
   VARIANT*    pvar  
);  
```  
  
#### 參數  
 `pExcepInfo`  
 \[out\] 包含報告的資訊的 `EXCEPINFO` 結構的指標是否找不到例外狀況處理常式。  
  
 `pvar`  
 \[in\] 值與例外狀況，例如 `throw` 陳述式擲回的值。  這個參數可以是 `NULL`。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|呼叫端可以處理例外狀況。|  
|`E_FAIL`|呼叫端不可以處理例外狀況。|  
  
## 備註  
 如果為 `IDispatchEx::InvokeEx`的呼叫或類似的方法，會造成例外狀況，指令碼引擎會檢查 `ICanHandleException` 支援介面的指令碼的呼叫端鏈結中的呼叫端並指出它可以處理例外狀況。  如果呼叫端不可以處理例外狀況，指令碼引擎會中止。  
  
## 請參閱  
 [ICanHandleException 介面](../../winscript/reference/icanhandleexception-interface.md)   
 [IDispatchEx::InvokeEx](../../winscript/reference/idispatchex-invokeex.md)