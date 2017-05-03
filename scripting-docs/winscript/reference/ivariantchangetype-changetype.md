---
title: "IVariantChangeType::ChangeType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IVariantChangeType::ChangeType"
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IVariantChangeType::ChangeType
使用不同的值並建立具有所指定型別的新 Variant。  
  
## 語法  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### 參數  
 `pvarDst`  
 \[in， out\] 包含值為的變數，表示 `pvarSrc`，但在 `vtNew`指定的型別。  
  
 `pvarSrc`  
 \[in\] 要變更之不同的值加入至新的型別。  
  
 `lcid`  
 \[in\] 所使用的地區設定內容時，將引數轉換成字串時。  
  
 `vtNew`  
 \[in\] 指定 `pvarDst` 會變成的型別。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 在原始值覆寫的情況下， `pvarDst` 和 `pvarSrc` 引數可能相等。  這個方法會傳遞至函式， `pvarDst` `VariantClear` ，因此應初始化 `pvarDst` 為有效值。  
  
## 請參閱  
 [IVariantChangeType 介面](../../winscript/reference/ivariantchangetype-interface.md)