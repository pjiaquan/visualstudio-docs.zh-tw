---
title: "IDispError::GetSource | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetSource
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetSource"
ms.assetid: 20def54c-a67c-4102-babf-6f0704e5fc5c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetSource
傳回引發錯誤的類別或應用程式的語言相關的程式設計識別項。  
  
## 語法  
  
```  
HRESULT GetSource(  
   BSTR*  pbstrSource  
);  
```  
  
#### 參數  
 `pbstrSource`  
 \[in\] 字串包含的程式設計識別項，其格式為 `progname.objectname`。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法可用來判斷發生例外狀況的類別或應用程式。  程式設計識別項在地區設定識別項所指定的語言可能會傳回在引動過程期間所提供的 \(LCID\)。  
  
> [!NOTE]
>  這個方法尚未實作。  
  
## 請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)