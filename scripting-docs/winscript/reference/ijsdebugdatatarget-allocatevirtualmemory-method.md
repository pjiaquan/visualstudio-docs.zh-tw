---
title: "IJsDebugDataTarget::AllocateVirtualMemory 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.AllocateVirtualMemory
apilocation: jscript9diag.dll
ms.assetid: 1d3a77b0-c1de-4a0c-a759-3e0c68fd96dd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::AllocateVirtualMemory 方法
保留和 \(或\) 認可目標處理序之虛擬位址空間中的記憶體區域。  
  
## 語法  
  
```  
HRESULT AllocateVirtualMemory(  
   UINT64 address,  
   DWORD size,  
   DWORD allocationType,  
   DWORD pageProtection,  
   UINT64 *pAllocatedAddress  
);  
```  
  
#### 參數  
 `address`  
 \[in\] 在應認可或保留記憶體的目標處理序中的位址。  這個值通常為零，在此情況下，系統會選擇位址。  
  
 `size`  
 \[in\] 要配置的記憶體區域大小 \(以位元組為單位\)。  系統會自動捨入為下一個分頁界限。  
  
 `allocationType`  
 \[in\] 表示要執行的配置類型。  這通常是 MEM\_COMMIT &#124; MEM\_RESERVE \(0x3000\)，在一個步驟中保留並認可配置。  
  
 `pageProtection`  
 \[in\] 要配置的頁面區域的記憶體保護。  如果要認可頁面，您可以指定任何一個記憶體保護常數 \(例如，PAGE\_READWRITE、PAGE\_EXECUTE\)。  
  
 `pAllocatedAddress`  
 \[out\] 頁面配置區域的基底位址。  
  
## 傳回值  
  
## 備註  
 除非使用 MEM\_RESET，否則函式會初始化其配置為零的記憶體。  如需詳細資訊，請參閱 VirtualAlloc Win32 API。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)