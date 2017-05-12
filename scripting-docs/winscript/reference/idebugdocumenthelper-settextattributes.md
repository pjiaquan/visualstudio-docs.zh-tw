---
title: "IDebugDocumentHelper::SetTextAttributes | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetTextAttributes
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetTextAttributes"
ms.assetid: 31657738-9e4c-436a-be61-23f4185d452e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetTextAttributes
將文字範圍的屬性，覆寫該文字的其他屬性。  
  
## 語法  
  
```  
HRESULT SetTextAttributes(  
   ULONG              ulCharOffset,  
   ULONG              cChars,  
   SOURCE_TEXT_ATTR*  pstaTextAttr  
);  
```  
  
#### 參數  
 `ulCharOffset`  
 \[in\] 文字範圍的開始位置。  
  
 `cChars`  
 \[in\] 字元數範圍的。  
  
 `pstaTextAttr`  
 \[in\] 文字範圍的原始程式文字屬性。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 是先前用來呼叫文字範圍的 `SetTextAttributes` 的錯誤文字加入至文件。  呼叫 `AddDBCSText`、 `AddUnicodeText`或 `AddDeferredText` 方法將文字加入至文件。  
  
## 請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE\_TEXT\_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)