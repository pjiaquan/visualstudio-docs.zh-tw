---
title: "IJsDebug::OpenVirtualProcess 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebug.OpenVirtualProcess
apilocation: jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebug::OpenVirtualProcess 方法
用來建立新的虛擬處理序物件的 Factory 方法。  
  
## 語法  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### 參數  
 `processId`  
 \[in\] 要用於附加偵錯工具的處理序 ID。  
  
 `runtimeJsBaseAddress`  
 \[in\] JavaScript 執行階段載入目標處理序的基底位址。  
  
 `pDataTarget`  
 \[in\] 偵錯工具提供的介面，用於查詢處理序狀態。  
  
 `ppProcess`  
 \[out\] 新增偵錯處理物件  
  
## 傳回值  
  
## 備註  
 如果 Jscript9diag 和 Jscript9 不相符，則傳回 E\_JsDEBUG\_MISMATCHED\_RUNTIME。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebug 介面](../../winscript/reference/ijsdebug-interface.md)