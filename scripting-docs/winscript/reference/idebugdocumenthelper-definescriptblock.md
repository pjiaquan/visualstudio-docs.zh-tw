---
title: "IDebugDocumentHelper::DefineScriptBlock | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.DefineScriptBlock
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::DefineScriptBlock"
ms.assetid: e4120377-f04f-44b1-950b-2beba06c9c12
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::DefineScriptBlock
指示 Helper 字元的特定範圍是由所指定的指令碼引擎處理的指令碼區塊。  
  
## 語法  
  
```  
HRESULT DefineScriptBlock(  
   ULONG           ulCharOffset,  
   ULONG           cChars,  
   IActiveScript*  pas,  
   BOOL            fScriptlet,  
   DWORD_PTR*      pdwSourceContext  
);  
```  
  
#### 參數  
 `ulCharOffset`  
 \[in\] 指令碼區塊的開始位置。  
  
 `cChars`  
 \[in\] 字元數量的指令碼區塊。  
  
 `pas`  
 \[out\] 此指令碼區塊的指令碼引擎。  
  
 `fScriptlet`  
 \[in\] 將旗標指出指令碼區塊是否 scriptlet。  
  
 `pdwSourceContext`  
 \[in\] 指令碼區塊的來源內容。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 其資料包含內嵌指令碼區塊時，智慧型主機可以使用這個方法。  其程式碼包含其他語言時，內嵌指令碼語言引擎就會使用這個方法。  
  
 指令碼引擎會在指令碼區塊中的任何語法配色和程式碼內容搜尋負責。  
  
 `DefineScriptBlock` 應呼叫方法，以加入文字之後 \(例如，使用 `IDebugDocumentHelper::AddDBCSText` 方法\)，但是，在指令碼區塊已剖析嗎 \(例如，使用 `IActiveScriptParse ::ParseScriptText` 方法\)。  
  
## 請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)