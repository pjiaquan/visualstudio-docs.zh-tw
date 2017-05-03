---
title: "IJsDebugDataTarget::ReadMemory 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadMemory
apilocation: jscript9diag.dll
ms.assetid: 664e0f7d-2007-45f4-b993-36fe8b1944e5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadMemory 方法
讀取目標處理序的記憶體。  
  
## 語法  
  
```  
HRESULT ReadMemory(  
   UINT64 address,  
   JsDebugReadMemoryFlags flags,  
   BYTE *pBuffer,  
   DWORD size,  
   DWORD *pBytesRead  
);  
```  
  
#### 參數  
 `address`  
 \[in\] 從其中讀取目標處理序記憶體的基底位址。  
  
 `flags`  
 \[in\] 控制 ReadMemory 行為的旗標。  
  
 `pBuffer`  
 \[out\] 從目標處理序的位址空間接收內容的緩衝區。  失敗時，這個緩衝區的內容未指定。  
  
 `size`  
 \[in\] 自處理序中讀取的位元組數。  
  
 `pBytesRead`  
 \[out\] 表示從目標處理序讀取的位元組數目。  如果清除 JsDebugAllowPartialRead，成功時，這個值將永遠與輸入大小完全相等。  如果已指定 JsDebugAllowPartialRead，成功時，這個值將會大於零。  
  
## 傳回值  
  
## 備註  
 成功時傳回 S\_OK，並對任何錯誤使用失敗碼。  如果位址無效，則傳回 E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS。  如需詳細資訊，請參閱 JsDebugAllowPartialRead。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)