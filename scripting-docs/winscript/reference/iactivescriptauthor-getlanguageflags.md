---
title: "IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetLanguageFlags
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetLanguageFlags"
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::GetLanguageFlags
傳回語言資訊。  
  
## 語法  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### 參數  
 `pgrfasa`  
 \[in\] 包含語言資訊的旗標。  可以是下列值的組合:  
  
|常數|值|描述|  
|--------|-------|--------|  
|fasaPreferInternalHandler|0x0001|這種語言所撰寫的指令碼引擎偏好指令碼事件處理常式建立而不是應用程式。|  
|fasaSupportInternalHandler|0x0002|語言支援 Scripting 指令碼中建立事件處理常式撰寫引擎。|  
|fasaCaseSensitive|0x0004|指令碼語言區分大小寫。|  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
 如果建立的指令碼引擎處理事件處理常式，您的應用程式應該呼叫 `IScriptEntry` 物件的 `CreateChildHandler` 。  這會對應到事件處理常式的 `IScriptScriptlet` 物件。  引擎也會加入事件處理常式加入至指令碼項目。  事件處理常式是包含指定的簽章資訊的空的函式。  
  
 如果您的應用程式處理事件處理常式，就應該呼叫從表示事件處理常式 scriptlet 的 `IScriptNode` 物件的 `CreateChildHandler` 。  這會建立與事件處理常式 scriptlet 的 `IScriptScriptlet` 物件。  應用程式也必須加入空的函式做為事件處理常式加入至新的或現有的 `IScriptEntry` 物件。  
  
## 請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)