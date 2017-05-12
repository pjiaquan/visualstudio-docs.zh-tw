---
title: "IJsDebugDataTarget 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: a9b784d6-958f-4d55-b3f6-c2d6b260a16b
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget 介面
由偵錯工具實作以提供存取和變更目標偵錯工具處理序狀態的功能。  
  
## 語法  
  
```  
IJsDebugDataTarget : public IUnknown;  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[IJsDebugDataTarget::AllocateVirtualMemory 方法](../../winscript/reference/ijsdebugdatatarget-allocatevirtualmemory-method.md)|保留和 \(或\) 認可目標處理序之虛擬位址空間中的記憶體區域。|  
|[IJsDebugDataTarget::CreateStackFrameEnumerator 方法](../../winscript/reference/ijsdebugdatatarget-createstackframeenumerator-method.md)|建立堆疊框架的列舉程式。|  
|[IJsDebugDataTarget::FreeVirtualMemory 方法](../../winscript/reference/ijsdebugdatatarget-freevirtualmemory-method.md)|釋放和 \(或\) 取消認可目標處理序之虛擬位址空間中的記憶體區域。|  
|[IJsDebugDataTarget::GetThreadContext 方法](../../winscript/reference/ijsdebugdatatarget-getthreadcontext-method.md)|擷取指定之執行緒的內容。|  
|[IJsDebugDataTarget::GetTlsValue 方法](../../winscript/reference/ijsdebugdatatarget-gettlsvalue-method.md)|對於要進行偵錯的執行緒，擷取執行緒區域儲存區 \(TLS\) 位置中所指定 TLS 索引的值。|  
|[IJsDebugDataTarget::ReadBSTR 方法](../../winscript/reference/ijsdebugdatatarget-readbstr-method.md)|從偵錯目標讀取 BSTR。|  
|[IJsDebugDataTarget::ReadMemory 方法](../../winscript/reference/ijsdebugdatatarget-readmemory-method.md)|讀取目標處理序的記憶體。|  
|[IJsDebugDataTarget::ReadNullTerminatedString 方法](../../winscript/reference/ijsdebugdatatarget-readnullterminatedstring-method.md)|從目標讀取指定數目的字元。|  
|[IJsDebugDataTarget::WriteMemory 方法](../../winscript/reference/ijsdebugdatatarget-writememory-method.md)|讀取目標處理序的記憶體。|  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)