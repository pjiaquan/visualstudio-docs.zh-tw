---
title: "IJsDebugDataTarget::WriteMemory 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.WriteMemory
apilocation: jscript9diag.dll
ms.assetid: 0d3c04c3-9ef8-4842-a145-3d29bca75062
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::WriteMemory 方法
讀取目標處理序的記憶體。  
  
## 語法  
  
```  
HRESULT WriteMemory(  
   UINT64 address,  
   const BYTE *pMemory,  
   DWORD size  
);  
```  
  
#### 參數  
 `address`  
 \[in\] 將目標處理序記憶體寫入其中的基底位址。  
  
 `pMemory`  
 \[in\] 要寫入到指定處理序的位址空間的資料。  
  
 `size`  
 \[in\] 要寫入處理序的位元組數目。  
  
## 傳回值  
  
## 備註  
 在傳送資料之前，系統會驗證在基底位址 \(Base Address\) 和指定大小記憶體中的所有資料是否可以寫入存取，如果無法存取，函式會引發 E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS 錯誤。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)