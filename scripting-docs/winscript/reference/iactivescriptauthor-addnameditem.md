---
title: "IActiveScriptAuthor::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddNamedItem"
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# IActiveScriptAuthor::AddNamedItem
加入根層級項目的名稱變更為撰寫引擎的命名空間的指令碼。  *根層次的* 項目是可以包含屬性和方法，，也可以包含事件來源的物件。  
  
## 語法  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### 參數  
 `pszName`  
 \[in\] 中的名稱範圍從指令碼。  這個名稱必須是唯一的、和永久性。  
  
 `dwFlags`  
 \[in\] 與具名項目的旗標。  可以是下列值的組合:  
  
|常數|值|描述|  
|--------|-------|--------|  
|SCRIPTITEM\_ISVISIBLE|0x00000002|表示項目的名稱可在指令碼的命名空間。  這允許對項目屬性、方法和事件的存取。<br /><br /> 依照慣例，項目的屬性包含項目的子成員。  因此，所有子物件屬性和方法 \(及其子成員，以遞迴方式\) 存取。|  
|SCRIPTITEM\_ISSOURCE|0x00000004|表示指令碼可以有指令碼事件處理常式的項目來源的事件。|  
|SCRIPTITEM\_GLOBALMEMBERS|0x00000008|指出這個項目是與指令碼相關聯的全域屬性的集合和方法。  它的成員會被建立為全域變數和方法。|  
|SCRIPTITEM\_ISPERSISTENT|0x00000040|表示應該儲存項目，如果建立的指令碼引擎會保留。|  
|SCRIPTITEM\_CODEONLY|0x00000200|表示具名項目表示一程式碼物件和它沒有建立的成員。|  
|SCRIPTITEM\_NOCODE|0x00000400|不表示具名項目是加入的名稱和它的建立。|  
  
 `pdisp`  
 \[out\] 用來收集方法、屬性或事件來源 `NamedItem` 物件的 `IDispatch` 。  
  
## 傳回值  
 `HRESULT`。  可能的值包括，，但不限於\)，這些在下表中。  
  
|值|描述|  
|-------|--------|  
|`S_OK`|方法成功。|  
  
## 備註  
  
## 請參閱  
 [IActiveScriptAuthor 介面](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)