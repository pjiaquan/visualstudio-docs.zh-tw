---
title: "IProvideExpressionContexts::EnumExpressionContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProvideExpressionContexts.EnumExpressionContexts
apilocation: jscript.dll
helpviewer_keywords: 
  - "IProvideExpressionContexts::EnumExpressionContexts"
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProvideExpressionContexts::EnumExpressionContexts
傳回運算式內容的列舉這個元件已知的。  
  
## 語法  
  
```  
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### 參數  
 `ppedec`  
 \[in\] 運算式內容的列舉這個元件已知的。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 同處理序偵錯處理常式會使用這個方法會尋找所有全域運算式內容與特定執行緒。  
  
> [!NOTE]
>  這個方法會從執行緒相關的內部。  它是由識別目前執行緒和傳回適當的列舉值的實作決定。  
  
## 請參閱  
 [IProvideExpressionContexts 介面](../../winscript/reference/iprovideexpressioncontexts-interface.md)