---
title: "IActiveScript::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Clone"
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::Clone
複製目前指令碼引擎 \(減去任何目前執行狀態\)，傳回沒有網站在目前執行緒上載入的指令碼引擎。  這個新的指令碼引擎屬性會與原始指令碼引擎是的屬性將會是相同的，如果轉換回這個初始狀態。  
  
## 語法  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### 參數  
 `ppscript`  
 \[out\] 接收指標複製的指令碼引擎的 [IActiveScript](../../winscript/reference/iactivescript.md) 介面變數的位址。  在這個初始狀態，因此，可以用之前，主應用程式必須建立網站和呼叫新指令碼引擎的 [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) 方法。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_NOTIMPL`|不支援這個方法。|  
|`E_POINTER`|無效的指標被指定。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎尚未載入或未初始化\)。|  
  
## 備註  
 `IActiveScript::Clone` 方法是 `IPersist*::Save`、 `CoCreateInstance`和 `IPersist*::Load`最佳化，所以，新指令碼引擎的狀態應該都相同，而且原始指令碼引擎的狀態在儲存和載入新的指令碼引擎。  將的項目複製的指令碼引擎，迴圈，但每個項目的特定物件指標忘記並取得與 [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) 方法。  允許對每個執行緒進入點 \(Apartment Model\) 的相同物件模型使用。  
  
 這個方法會提供可以在相同指令碼的多個執行個體的多執行緒的伺服器主應用程式使用。  指令碼引擎可能會傳回 `E_NOTIMPL`，在這種情況下，主應用程式可以藉由重複這個持續性 \(Persistent\) 狀態和建立指令碼引擎的新執行個體達到相同的結果對應項 `IPersist*` 介面的。  
  
 這個方法只能從非 Base 執行緒呼叫未使非基底 Callout 裝載物件或加入至 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) 介面。  
  
## 請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)