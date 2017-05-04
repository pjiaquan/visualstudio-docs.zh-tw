---
title: "IActiveScriptSite::GetItemInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSite.GetItemInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSite_GetItemInfo"
ms.assetid: f859ed3b-02c1-4924-99f8-5f5bf1bf8405
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSite::GetItemInfo
允許指令碼引擎取得項目相關資訊以 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 方法。  
  
## 語法  
  
```  
HRESULT GetItemInfo(  
    LPCOLESTR pstrName,     // address of item name  
    DWORD dwReturnMask,     // bit mask for information retrieval  
    IUnknown **ppunkItem,   // address of pointer to item's IUnknown  
    ITypeInfo **ppTypeInfo  // address of pointer to item's ITypeInfo  
);  
```  
  
#### 參數  
 `pstrName`  
 \[out\] 此名稱與項目，在 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 方法上指定。  
  
 `dwReturnMask`  
 \[in\] 位元遮罩指定應該傳回關於項目的資訊。  指令碼引擎需要最少資訊量，因為某些傳回參數 \(例如， `ITypeInfo`\) 可能需要相當長的時間載入或產生。  可以是下列值的組合:  
  
|值|意義|  
|-------|--------|  
|SCRIPTINFO\_IUNKNOWN|傳回這個項目的 `IUnknown` 介面。|  
|SCRIPTINFO\_ITYPEINFO|傳回這個項目的 `ITypeInfo` 介面。|  
  
 `ppunkItem`  
 \[out\] 接收 `IUnknown` 介面指標變數的位址與指定項目的。  指令碼引擎可以使用 `IUnknown::QueryInterface` 方法取得項目的 `IDispatch` 介面。  如果 `dwReturnMask` 不包括 SCRIPTINFO\_IUNKNOWN 值，這個參數會收到 null。  此外，;如果沒有任何物件與項目名稱，會收到 null;，當具名項目已加入與 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) 方法，設定的 SCRIPTITEM\_CODEONLY 旗標這個機制來建立簡單的類別。  
  
 `ppTypeInfo`  
 \[out\] 接收 `ITypeInfo` 介面指標變數的位址相關聯的項目。  這個參數接收，則為 null `dwReturnMask` SCRIPTINFO\_ITYPEINFO 不包含值，則為，如果型別資訊對這個項目無法使用。  如果型別資訊無法使用，則該物件不能做為事件來源，，且必須實現繫結名稱與 `IDispatch::GetIDsOfNames` 方法。  請注意擷取的 `ITypeInfo` 介面描述項目的 Coclass \(TKIND\_COCLASS\)，因為物件可以支援多個介面及事件介面。  如果項目 `IProvideMultipleTypeInfo` 支援介面，擷取的 `ITypeInfo` 介面是使用 `IProvideMultipleTypeInfo::GetInfoOfIndex` 方法，做為索引以零 `ITypeInfo` 會收到的相同。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數無效。|  
|`E_POINTER`|無效的指標被指定。|  
|`TYPE_E_ELEMENTNOTFOUND`|找不到指定名稱的項目。|  
  
## 備註  
 這個方法會擷取 `dwReturnMask` 參數運算式的相關資訊，這會增加效能。  例如，如果 `ITypeInfo` 介面，為項目不需要，在 `dwReturnMask`未指定。  
  
## 請參閱  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)