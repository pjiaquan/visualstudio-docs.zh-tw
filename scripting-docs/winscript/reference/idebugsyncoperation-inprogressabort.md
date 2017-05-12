---
title: "IDebugSyncOperation::InProgressAbort | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugSyncOperation.InProgressAbort
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugSyncOperation::InProgressAbort"
ms.assetid: bfd0889c-b627-4843-b1c6-b6b918f42d61
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation::InProgressAbort
取消作業正在進行中的另一個執行緒。  
  
## 語法  
  
```  
HRESULT InProgressAbort();  
```  
  
#### 參數  
 這個方法不採用參數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|作業無法取消。|  
|`E_ABORT`|作業無法完成。|  
  
## 備註  
 同處理序偵錯此處理常式便會呼叫這個方法會從偵錯工具執行緒內移除正在另一個執行緒執行作業。  
  
 如果 `InProgressAbort` 方法無法完成作業，它會盡快傳回 `E_ABORT` 。  如果作業無法取消，這個方法會傳回 `E_NOTIMPL` 。  
  
## 請參閱  
 [IDebugSyncOperation 介面](../../winscript/reference/idebugsyncoperation-interface.md)