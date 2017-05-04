---
title: "IJsDebugDataTarget::ReadNullTerminatedString 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadNullTerminatedString
apilocation: jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugDataTarget::ReadNullTerminatedString 方法
從目標讀取指定數目的字元。  
  
## 語法  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### 參數  
 `address`  
 \[in\] 要用於讀取的位址。  
  
 `characterSize`  
 \[in\] 字串中每個字元的大小。  
  
 `maxCharacters`  
 \[in\] 讀取的字元數上限。maxCharacters 應是合理的。  所有超過 128MB 記憶體的要求都會失敗。如果字串大於 maxCharacters，則結果字串會在 maxCharacters 之後遭截斷。  
  
 `pString`  
 \[out\] 從目標讀取的 BSTR。  
  
## 傳回值  
  
## 備註  
 如果已截斷，則傳回 S\_FALSE。  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugDataTarget 介面](../../winscript/reference/ijsdebugdatatarget-interface.md)