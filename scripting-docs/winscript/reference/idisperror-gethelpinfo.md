---
title: "IDispError::GetHelpInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispError.GetHelpInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IDispError::GetHelpInfo"
ms.assetid: a146df13-eda4-4e56-8bf0-cf9886a2150f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispError::GetHelpInfo
如果可能傳回說明檔和說明錯誤主題代碼的路徑。  
  
## 語法  
  
```  
HRESULT GetHelpInfo(  
   BSTR*  pbstrFileName,  
   DWORD*  pdwContext  
);  
```  
  
#### 參數  
 `pbstrFileName`  
 \[in\] 包含說明檔的完整路徑的字串。  如果沒有說明檔或發生錯誤，則傳回值為 NULL。  
  
 `pdwContext`  
 \[in\] 錯誤的說明主題代碼。  如果沒有說明檔 \(如果 `pbstrFileName` 是空的\)，此參數就沒有任何意義。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_FAIL`|特定提供者時發生錯誤。|  
|`E_INVALIDARG`|`pbstrFileName` 或 `pdwContext` 是空的。|  
|`E_OUTOFMEMORY`|提供者無法配置傳回說明檔路徑的足夠的記憶體。|  
  
## 備註  
 如果這個方法會傳回可說明檔和說明錯誤主題代碼的路徑。  
  
> [!NOTE]
>  這個方法尚未實作。  
  
## 請參閱  
 [IDispError 介面](../../winscript/reference/idisperror-interface.md)