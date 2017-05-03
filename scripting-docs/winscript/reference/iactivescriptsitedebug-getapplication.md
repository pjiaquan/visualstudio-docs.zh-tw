---
title: "IActiveScriptSiteDebug::GetApplication | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetApplication
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetApplication"
ms.assetid: 4400f1b1-3108-4a71-b1f1-43586fe1227c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetApplication
傳回應用程式進行偵錯的物件與這個指令碼網站。  
  
## 語法  
  
```  
HRESULT GetApplication(  
   IDebugApplication**  ppda  
);  
```  
  
#### 參數  
 `ppda`  
 \[in\] 偵錯應用程式的物件指標與指令碼相關聯的網站。  
  
## 傳回值  
 方法會傳回 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
|`E_NOTIMPL`|主應用程式並不直接支援偵錯。|  
  
## 備註  
 `GetApplication` 方法為智慧型主機提供一種方法來定義每個指令碼所屬的應用程式物件。  如果失敗，指令碼引擎應該嘗試呼叫這個方法會為其包含的應用程式和表示 `IProcessDebugManager::GetDefaultApplication` 。  
  
## 請參閱  
 [IActiveScriptSiteDebug 介面](../../winscript/reference/iactivescriptsitedebug-interface.md)   
 [IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)