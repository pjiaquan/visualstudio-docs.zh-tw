---
title: "IDebugDocumentHost::GetDeferredText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHost.GetDeferredText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDebugDocumentHost::GetDeferredText"
ms.assetid: 527da666-fef5-4db3-a319-e68d466a7721
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost::GetDeferredText
使用方法，將 `IDebugDocumentHelper::AddDeferredText` 傳回字元的範圍，原始主應用程式文件。  
  
## 語法  
  
```  
HRESULT GetDeferredText(  
   DWORD              dwTextStartCookie,  
   WCHAR*             pcharText,  
   SOURCE_TEXT_ATTR*  pstaTextAttr,  
   ULONG*             pcNumChars,  
   ULONG              cMaxChars  
);  
```  
  
#### 參數  
 `dwTextStartCookie`  
 \[in\] 表示文字的開始位置的主應用程式定義的 Cookie。  
  
 `pcharText`  
 \[in， out\] A 字元文字緩衝區。  如果這個參數是 `NULL`，這個方法不會傳回字元。  
  
 `pstaTextAttr`  
 \[in， out\] A 字元屬性緩衝區。  如果這個參數是 `NULL`，這個方法不會傳回屬性。  
  
 `pcNumChars`  
 \[in， out\] 表示傳回的字元\/屬性的實際數目。  必須將這個參數設為零在呼叫之前這個方法。  
  
 `cMaxChars`  
 \[out\] 傳回的最大字元數。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|未實作這個方法。|  
  
## 備註  
 如果主應用程式不會呼叫 `IDebugDocumentHelper::AddDeferredText`，這個方法可能會傳回 `E_NOTIMPL`。  
  
> [!NOTE]
>  這個方法會從原始文件中的文字。  主機不會追蹤編輯或其他變更至文件。  
  
## 請參閱  
 [IDebugDocumentHost 介面](../../winscript/reference/idebugdocumenthost-interface.md)   
 [IDebugDocumentHelper::AddDeferredText](../../winscript/reference/idebugdocumenthelper-adddeferredtext.md)   
 [SOURCE\_TEXT\_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)