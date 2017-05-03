---
title: "IActiveScriptStats::GetStat | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStat
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStat"
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStat
標準指令碼統計資料的傳回。  
  
## 語法  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### 參數  
 `stid`  
 \[in\] 指定要傳回的哪個統計資料。  必須是一個值:  
  
|常數|值|描述|  
|--------|-------|--------|  
|SCRIPTSTAT\_STATEMENT\_COUNT|1|因為指令碼啟動的統計或重設，則會傳回要執行的陳述式數目。|  
  
 `pluHi`  
 \[in\] 表示統計資料的 64 位元不帶正負號的整數的高 32 位元。  
  
 `pluLo`  
 \[in\] 表示統計資料的 64 位元不帶正負號的整數的低 32 位元。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括下表所列，，但不限於\) 值。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會傳回其中一個標準指令碼統計資料。  
  
## 請參閱  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats 介面](../../winscript/reference/iactivescriptstats-interface.md)