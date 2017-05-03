---
title: "IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDebugHelper.CreatePropertyBrowserEx
apilocation: pdm.dll
helpviewer_keywords: 
  - "IDebugHelper::CreatePropertyBrowserEx"
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugHelper::CreatePropertyBrowserEx
傳回包裝變數並允許不同的 VARTYPE 值或型別的自訂轉換為字串的屬性瀏覽器中。  
  
## 語法  
  
```  
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
   IDebugProperty**          ppdob  
);  
```  
  
#### 參數  
 `pvar`  
 \[in\] 要瀏覽的根 Variant。  
  
 `bstrName`  
 \[in\] 要寫入根目錄的名稱。  
  
 `pdat`  
 \[in\] 執行緒在哪些需求屬性。  如果這個參數為 null，構成不執行任何動作。  
  
 `pdf`  
 \[in\] 則為 Variant 提供自訂格式化。  
  
 `ppdob`  
 \[in\] 屬性瀏覽器。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會傳回包裝變數並允許不同的 VARTYPE 值或型別的自訂轉換為字串的屬性瀏覽器中。  
  
## 請參閱  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [IDebugHelper 介面](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty 介面](../../winscript/reference/idebugproperty-interface.md)