---
title: "IDispatchEx::GetDispID | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetDispID
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetDispID 方法"
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetDispID
將單一成員名稱與其對應的 DISPID，在 \[ `IDispatchEx::InvokeEx`的後續呼叫會接著使用。  
  
## 語法  
  
```  
 HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### 參數  
 `bstrName`  
 藉由在要對應的名稱。  
  
 `grfdex`  
 判斷取得成員識別項的選項。  這可以是下列值的組合:  
  
|值|意義|  
|-------|--------|  
|fdexNameCaseSensitive|該要求的名稱搜尋完成以區分大小寫。  支援以不區分大小寫的查詢的物件會忽略。|  
|fdexNameEnsure|這個成員建立的要求，如果檔案不存在。  新的成員應該會以的值 `VT_EMPTY`。|  
|fdexNameImplicit|指示呼叫端搜尋物件特定名稱的成員，而基底物件未明確指定。|  
|fdexNameCaseInsensitive|該名稱的要求完成搜尋不區分大小寫的方式。  由不支援不區分大小寫的查詢的物件會忽略。|  
  
 `pid`  
 out 接收 DISPID 結果的呼叫端配置之位置的指標。  如果發生錯誤， `pid` 包含 DISPID\_UNKNOWN。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`E_OUTOFMEMORY`|記憶體不足。|  
|`DISP_E_UNKNOWNNAME`|名稱不明。|  
  
## 備註  
 `GetDispID` 可以用來代替 `GetIDsOfNames` 取得指定成員的 DISPID。  
  
 由於 `IDispatchEx` 允許成員的加入和刪除，這組 DISPID 維持不變在物件的存留期。  
  
 移除在 `IDispatch::GetIDsOfNames` 中未使用的 `riid` 參數。  
  
## 範例  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## 請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)