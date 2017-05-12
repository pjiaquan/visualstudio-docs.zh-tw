---
title: "IDispatchEx::GetMemberProperties | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetMemberProperties
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetMemberProperties 方法"
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetMemberProperties
擷取成員的屬性。  
  
## 語法  
  
```  
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### 參數  
 `id`  
 辨識成員。  使用 `GetDispID` 或 `GetNextDispID` 取得分派識別項。  
  
 `grfdexFetch`  
 決定要擷取哪些屬性。  這可以是值的組合列於下 `pgrfdex` 和\/或下列值的組合:  
  
|值|意義|  
|-------|--------|  
|grfdexPropCanAll|合併 fdexPropCanGet fdexPropCanPut fdexPropCanPutRef、、、、和 fdexPropCanCall fdexPropCanConstruct fdexPropCanSourceEvents。|  
|grfdexPropCannotAll|合併 fdexPropCannotGet fdexPropCannotPut fdexPropCannotPutRef、、、、和 fdexPropCannotCall fdexPropCannotConstruct fdexPropCannotSourceEvents。|  
|grfdexPropExtraAll|組合 fdexPropNoSideEffects 和 fdexPropDynamicType。|  
|grfdexPropAll|合併 grfdexPropCanAll、grfdexPropCannotAll 和 grfdexPropExtraAll。|  
  
 `pgrfdex`  
 接收要求的屬性 `DWORD` 的位址。  這可以是下列值的組合:  
  
|值|意義|  
|-------|--------|  
|fdexPropCanGet|使用 DISPATCH\_PROPERTYGET，成員可以取得。|  
|fdexPropCannotGet|使用 DISPATCH\_PROPERTYGET，成員無法取得。|  
|fdexPropCanPut|使用 DISPATCH\_PROPERTYPUT，成員可以設定為。|  
|fdexPropCannotPut|使用 DISPATCH\_PROPERTYPUT，成員無法設定。|  
|fdexPropCanPutRef|使用 DISPATCH\_PROPERTYPUTREF，成員可以設定為。|  
|fdexPropCannotPutRef|使用 DISPATCH\_PROPERTYPUTREF，成員無法設定。|  
|fdexPropNoSideEffects|這個成員沒有任何副作用 \(Side Effect\)。  例如，偵錯工具可以安全地取得\/設定\/呼叫這個成員不會變更偵錯指令碼的狀態。|  
|fdexPropDynamicType|在物件的存留期 \(Lifetime\) 內，這個成員是動態的，而且可以變更。|  
|fdexPropCanCall|使用 DISPATCH\_METHOD，成員可以呼叫做為方法。|  
|fdexPropCannotCall|使用 DISPATCH\_METHOD，成員不能做為方法。|  
|fdexPropCanConstruct|使用 DISPATCH\_CONSTRUCT，成員可以呼叫做為建構函式。|  
|fdexPropCannotConstruct|使用 DISPATCH\_CONSTRUCT，成員無法呼叫為建構函式。|  
|fdexPropCanSourceEvents|這個成員可以引發事件。|  
|fdexPropCannotSourceEvents|這個成員無法引發事件。|  
  
## 傳回值  
 下列值的傳回一個值:  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|`DISP_E_UNKNOWNNAME`|名稱不明。|  
  
## 範例  
  
```  
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## 請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)