---
title: "IJsDebugProcess::CreateBreakPoint 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateBreakPoint
apilocation: jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IJsDebugProcess::CreateBreakPoint 方法
將中斷點置於指定的文件位置。  
  
## 語法  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### 參數  
 `documentId`  
 \[in\] IDebugDocumentText 的指標。  
  
 `characterOffset`  
 \[in\] 從檔案開頭開始的字元位移。  
  
 `characterCount`  
 \[in\] 應插入中斷點的文件文字的長度。  
  
 `isEnabled`  
 \[in\] 指定是否啟用中斷點。  
  
 `ppDebugBreakPoint`  
 \[out\] 代表所建立之中斷點的物件。  
  
## 傳回值  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugProcess 介面](../../winscript/reference/ijsdebugprocess-interface.md)