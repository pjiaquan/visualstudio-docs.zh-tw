---
title: "JsDebugReadMemoryFlags 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugReadMemoryFlags
apilocation: jscript9diag.dll
ms.assetid: 0d98d154-9cb1-49de-b2df-a2d029d343b7
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# JsDebugReadMemoryFlags 列舉
旗標，用於指定讀取記憶體時的行為。  
  
## 語法  
  
```  
enum JsDebugReadMemoryFlags  
{  
   None = 0,  
   JsDebugAllowPartialRead= 0x1  
} JsDebugReadMemoryFlags;  
```  
  
## Members  
  
### 值  
  
|名稱|描述|  
|--------|--------|  
|`JsDebugAllowPartialRead`|表示呼叫端想要在只有一部分記憶體讀取成功時，讓讀取作業成功。  如果已設定此項，則只有在 'Address' 無效時才會引發 E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS 錯誤。  如果清除這個旗標，則所要求記憶體的任何部分無法讀取時，會引發 E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS 錯誤。|  
|`None`|表示呼叫端想要 ReadMemory 的預設行為。|  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [Windows 指令碼介面參考](../../winscript/reference/windows-script-interfaces-reference.md)