---
title: "IActiveScript::AddNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "AddNamedItem 方法, IActiveScript 介面"
ms.assetid: a7c6317d-948f-4bb3-b169-1bbe5b7c7cc5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddNamedItem
加入根層級項目的名稱加入至指令碼引擎的命名空間。  根層次的項目就是具有屬性的物件和方法，事件來源，或全部三個  
  
## 語法  
  
```  
HRESULT AddNamedItem(  
    LPCOLESTR pstrName,  // address of item name  
    DWORD dwFlags          // item flags  
);  
```  
  
#### 參數  
 `pstrName`  
 \[in\] 包含項目的名稱範圍從指令碼緩衝區的位址。  這個名稱必須是唯一的、和永久性。  
  
 `dwFlags`  
 \[in\] 旗標與項目。  可以是下列值的組合:  
  
|值|意義|  
|-------|--------|  
|SCRIPTITEM\_CODEONLY|表示具名項目表示一行程式碼，物件，而且未 `IUnknown` 將要與這個程式碼物件。  主應用程式只有一個名稱就是這個物件。  在物件導向語言 \(例如 C\+\+ 中，這個旗標會建立類別。  並非所有語言都支援這個旗標。|  
|SCRIPTITEM\_GLOBALMEMBERS|表示項目是全域屬性 \(Property\) 和方法的集合與指令碼相關聯的。  通常，一個指令碼引擎會忽略物件名稱 \(除了使用其用途以外的做為 Cookie [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) 方法的，或解析的明確檢視\) 並公開其成員當做全域變數和方法。  如此可讓主應用程式傳遞給指令碼擴充可用程式庫 \(執行階段函式等等\)。  它會留給指令碼引擎處理名稱衝突 \(例如，在中，當兩個 SCRIPTITEM\_GLOBALMEMBERS 項目具有相同名稱的方法\)，因此，雖然錯誤不應該是傳回的情況。|  
|SCRIPTITEM\_ISPERSISTENT|表示應該儲存項目，如果指令碼引擎會保留。  同樣地，設定這個旗標指示回這個初始狀態的轉換應該保留項目的名稱和型別資訊，不過， \(指令碼引擎必須釋放所有指標會實際物件的介面\)。|  
|SCRIPTITEM\_ISSOURCE|表示指令碼可以接收的項目來源事件。  子物件 \(在它們自己的物件\) 之物件的屬性也可以做為事件來源的指令碼。  這不是遞迴的，不過，它是常見的執行個體，例如，建立容器及其所有便利機制其成員的控制項。|  
|SCRIPTITEM\_ISVISIBLE|表示項目的名稱可在指令碼的命名空間，允許存取屬性，項目的方法和事件。  這個項目的屬性包含項目的子系，因此，所有子物件屬性和方法 \(及其子系，遞迴地\) 來存取。|  
|SCRIPTITEM\_NOCODE|表示項目是加入指令碼的命名空間名稱，而且不應該被視為程式碼應該相關聯的項目。  例如，在中，不需要設定這個旗標， VBScript 將建立具名項目的其他模組中， C\+\+，而且可能會建立具名項目的個別的包裝函式類別。|  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|無效的指標被指定。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎尚未載入或未初始化\)。|  
  
## 請參閱  
 [IActiveScript](../../winscript/reference/iactivescript.md)