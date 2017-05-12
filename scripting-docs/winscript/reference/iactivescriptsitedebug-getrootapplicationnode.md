---
title: "IActiveScriptSiteDebug::GetRootApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetRootApplicationNode
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetRootApplicationNode"
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetRootApplicationNode
取得下一個指令碼檔應該加入的應用程式節點。  
  
## 語法  
  
```  
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### 參數  
 `ppdanRoot`  
 \[in\] 保留指令碼檔案的偵錯應用程式的節點。  可以是 `NULL`。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 這個方法會傳回下一個指令碼檔應該加入的應用程式節點。  如果指令碼檔應該位於最上層，則方法會傳回 `ppdanRoot` 的 `NULL` 。  
  
## 請參閱  
 [IActiveScriptSiteDebug 介面](../../winscript/reference/iactivescriptsitedebug-interface.md)