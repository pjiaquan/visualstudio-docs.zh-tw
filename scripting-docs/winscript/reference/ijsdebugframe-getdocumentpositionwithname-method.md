---
title: "IJsDebugFrame::GetDocumentPositionWithName 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetDocumentPositionWithName 方法
在使用者文件中傳回此堆疊框架目前的位置。  
  
## 語法  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### 參數  
 `pDocumentName`  
 \[out\] 若為靜態指令碼，即為文件的 URL。  針對動態指令碼，會傳回包含指令碼類型 \(例如，評估程式碼，函式程式碼等\) 的名稱。  
  
 `pLine`  
 \[out\] 文件中以 1為起始的行位置。  
  
 `pColumn`  
 \[out\] 文件中以 1為起始的行位置。  
  
## 傳回值  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)