---
title: "IJsDebugFrame::GetDocumentPositionWithId 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithId
apilocation: jscript9diag.dll
ms.assetid: 48f8eb26-8ae4-4d5c-bd94-796023b03bcb
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IJsDebugFrame::GetDocumentPositionWithId 方法
在使用者文件中傳回此堆疊框架目前的位置。  
  
## 語法  
  
```  
HRESULT GetDocumentPositionWithId(  
   UINT64 *pDocumentId,  
   DWORD *pCharacterOffset,  
   DWORD *pStatementCharCount  
);  
```  
  
#### 參數  
 `pDocumentId`  
 \[out\] 原始文件的唯一識別碼 \(IDebugDocumentText 的指標\)。  
  
 `pCharacterOffset`  
 \[out\] 從指令碼開頭位移的以零起始的字元。  
  
 `pStatementCharCount`  
 \[out\] 目前陳述式的長度，從 \*pCharacterOffset 開始，以字元為單位。  
  
## 傳回值  
  
## 需求  
 **標頭：**jscript9diag.h  
  
## 請參閱  
 [IJsDebugFrame 介面](../../winscript/reference/ijsdebugframe-interface.md)