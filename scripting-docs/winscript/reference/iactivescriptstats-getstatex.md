---
title: "IActiveScriptStats::GetStatEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStatEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStatEx"
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStatEx
傳回自訂指令碼統計資料。  
  
## 語法  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### 參數  
 `guid`  
 \[in\] 指定要傳回的哪個統計資料。  統計資料對應至特定 GUID 完全引擎已定義的語意。  
  
 `pluHi`  
 \[in\] 表示統計資料的 64 位元不帶正負號的整數的高 32 位元。  
  
 `pluLo`  
 \[in\] 表示統計資料的 64 位元不帶正負號的整數的低 32 位元。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|未實作這個方法。|  
  
## 備註  
 這個方法允許自訂指令碼引擎會統計有意義之自訂主應用程式。  
  
> [!NOTE]
>  此方法目前尚未實作。  
  
## 請參閱  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats 介面](../../winscript/reference/iactivescriptstats-interface.md)