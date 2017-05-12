---
title: "IRemoteDebugApplicationEx:SetLocale | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IRemoteDebugApplicationEx:SetLocale
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IRemoteDebugApplicationEx:SetLocale"
ms.assetid: cd19f725-f4cd-453a-95e1-0bad676451da
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IRemoteDebugApplicationEx:SetLocale
設定偵錯工具當地語系化的語言。  
  
## 語法  
  
```  
HRESULT SetLocale(  
   DWORD  dwLangID  
);  
```  
  
#### 參數  
 `dwLangID`  
 \[in\] 語言 ID。.  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [ISetNextStatement 介面](../../winscript/reference/isetnextstatement-interface.md)