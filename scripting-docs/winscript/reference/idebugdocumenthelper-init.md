---
title: "IDebugDocumentHelper::Init | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.Init
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::Init"
ms.assetid: 1dd5a01f-0779-4109-8c6c-f16f5a3835bf
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::Init
`Init` 方法初始化具有名稱和初始屬性的偵錯資料 Helper。  
  
## 語法  
  
```  
HRESULT Init(  
   IDebugApplication*  pda,  
   LPCOLESTR           pszShortName,  
   LPCOLESTR           pszLongName,  
   TEXT_DOC_ATTR       docAttr  
);  
```  
  
#### 參數  
 `pda`  
 \[in\] 偵錯應用程式與文件相關聯的。  
  
 `pszShortName`  
 \[in\] null 結尾包含文件的簡短名稱的字串。  
  
 `pszLongName`  
 \[in\] null 結尾包含文件的完整名稱的字串。  
  
 `docAttr`  
 \[in\] 指定 Word 文件屬性。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會初始化具有名稱和初始屬性的偵錯資料 Helper。  
  
 文件不會出現在樹狀目錄，直到 `IDebugDocumentHelper::Attach` 呼叫。  
  
## 請參閱  
 [IDebugDocumentHelper::Attach](../../winscript/reference/idebugdocumenthelper-attach.md)   
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [TEXT\_DOC\_ATTR 的常數](../../winscript/reference/text-doc-attr-constants.md)