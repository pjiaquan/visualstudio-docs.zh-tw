---
title: "IDebugStackFrameSnifferEx::EnumStackFramesEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugStackFrameSnifferEx.EnumStackFramesEx
apilocation: jscript.dll
helpviewer_keywords: 
  - "IDebugStackFrameSnifferEx::EnumStackFramesEx"
ms.assetid: b656b581-aff0-4984-8d8a-a1c7a8e6558a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugStackFrameSnifferEx::EnumStackFramesEx
傳回堆疊框架的列舉值目前執行緒的。  
  
## 語法  
  
```  
HRESULT EnumStackFramesEx(  
   DWORD_PTR                dwSpMin,  
   IEnumDebugStackFrames**  ppedsf  
);  
```  
  
#### 參數  
 `dwSpMin`  
 \[in\] 列舉型別的堆疊框架下方位址限制。  
  
 `ppedsf`  
 \[out\] 堆疊框架的列舉值目前執行緒的。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 堆疊框架列舉值傳回開始堆疊最上方的框架，與最近推入的框架。  列舉值包含位址大於或等於 `dwSpMin`只的堆疊框架。  
  
## 請參閱  
 [IDebugStackFrameSnifferEx 介面](../../winscript/reference/idebugstackframesnifferex-interface.md)