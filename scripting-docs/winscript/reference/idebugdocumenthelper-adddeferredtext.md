---
title: "IDebugDocumentHelper::AddDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.AddDeferredText
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::AddDeferredText"
ms.assetid: 9463cfb0-76cc-45ee-b32c-f37dce2b2e0e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::AddDeferredText
告知 Helper 指定可用的文字，不過，它不會提供字元。  
  
## 語法  
  
```  
HRESULT AddDeferredText(  
   ULONG  cChars,  
   DWORD  dwTextStartCookie  
);  
```  
  
#### 參數  
 `cChars`  
 \[out\] \(會加入\) 的 Unicode 字元數。  
  
 `dwTextStartCookie`  
 \[in\] 表示文字的開始位置的主應用程式定義的 Cookie。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|失敗的方法。|  
  
## 備註  
 這個方法可讓主應用程式提供延後加入字元，除非必要，，同時讓 Helper 產生正確告知和大小資訊時。  `dwTextStartCookie` 參數是 Cookie，定義由主機，表示文字的開始位置。  `IDebugDocumentText::GetText` 對的後續呼叫必須提供這個 Cookie。  例如，在表示 DBCS 之文字的主機， Cookie 可以是位移的位元組。  
  
 假設， `IDebugDocumentText::GetText` 對的單一呼叫可從多個呼叫會 `AddDeferredText`字元。  Helper 類別可以多次也要求延後的相同字元範圍。  
  
> [!NOTE]
>  不應該與 `AddUnicodeText` 或 `AddDBCSText`的呼叫混合\] `AddDeferredText` 的呼叫。  如果發生這種情況， `E_FAIL` 傳回。  
  
## 請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [IDebugDocumentHelper::AddUnicodeText](../../winscript/reference/idebugdocumenthelper-addunicodetext.md)   
 [IDebugDocumentHelper::AddDBCSText](../../winscript/reference/idebugdocumenthelper-adddbcstext.md)   
 [IDebugDocumentText::GetText](../../winscript/reference/idebugdocumenttext-gettext.md)