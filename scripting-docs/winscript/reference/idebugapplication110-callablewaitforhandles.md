---
title: "IDebugApplication110::CallableWaitForHandles | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplication110::CallableWaitForHandles"
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugApplication110::CallableWaitForHandles
等候任何指定的控制代碼都收到信號時，允許跨執行緒呼叫張貼至這個執行緒時。  必須從偵錯工具執行緒呼叫這個方法。  
  
> [!IMPORTANT]
>  [IDebugApplication110 介面](../../winscript/reference/idebugapplication110-interface.md) 由 PDM v11.0 實作和更大。  位於 activdbg100.h。  
  
## 語法  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
  
```  
  
#### 參數  
 `handleCount`  
 等候控制代碼的數目。  
  
 `pHandles`  
 等候控制代碼的集合。  
  
 `pIndex`  
 當 HRESULT 值為 S\_OK，索引設定為之控制代碼的 `pHandles` 中。  
  
## 請參閱  
 [IDebugApplication110 介面](../../winscript/reference/idebugapplication110-interface.md)