---
title: "IDebugDocumentHelper::SetDefaultTextAttr | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugDocumentHelper.SetDefaultTextAttr
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugDocumentHelper::SetDefaultTextAttr"
ms.assetid: 019a4191-0019-4376-bf70-89b33e7369de
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHelper::SetDefaultTextAttr
設定預設的屬性已不在指令碼區塊中的文字。  
  
## 語法  
  
```  
HRESULT SetDefaultTextAttr(  
   SOURCE_TEXT_ATTR  staTextAttr  
);  
```  
  
#### 參數  
 `staTextAttr`  
 預設來源文字屬性。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 除非由這個方法會變更預設屬性，則文字的預設屬性在指令碼區塊外 SOURCETEXT\_ATTR\_NONSOURCE。  使用者介面可以使用這項資訊指示文字外部指令碼區塊標記為唯讀。  
  
## 請參閱  
 [IDebugDocumentHelper 介面](../../winscript/reference/idebugdocumenthelper-interface.md)   
 [SOURCE\_TEXT\_ATTR 列舉](../../winscript/reference/source-text-attr-enumeration.md)