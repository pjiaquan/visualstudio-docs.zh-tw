---
title: "IJsDebugDataTarget::FreeVirtualMemory 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.FreeVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: ea54bad3-9ae3-436b-974d-70fc7fffefd6
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::FreeVirtualMemory 方法
釋放和 \(或\) 取消認可目標處理序之虛擬位址空間中的記憶體區域。  
  
## 語法  
  
```  
HRESULT FreeVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD freeType  
);  
```  
  
#### 參數  
 `address`  
 \[in\] 在應釋放記憶體的目標處理序中的位址。  
  
 `size`  
 \[in\] 要取消認可的位元組數。  若要釋放記憶體區域，這個值必須是零。  
  
 `freeType`  
 \[in\] 表示要執行的可用作業類型。  這通常是 MEM\_RELEASE \(0x8000\)，釋放分頁的指定區域。  在作業之後，頁面會處於可用狀態。  可以改用 MEM\_DECOMMIT \(0x4000\) 來取消認可頁面，而不將其釋放。  
  
## 傳回值  
  
## 備註  
 如需詳細資訊，請參閱 VirtualFree Win32 API。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)