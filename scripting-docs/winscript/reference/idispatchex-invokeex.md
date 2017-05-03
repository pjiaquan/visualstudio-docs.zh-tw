---
title: "IDispatchEx::InvokeEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.InvokeEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "InvokeEx 方法"
ms.assetid: d90783e6-4b89-4423-8a56-a9c8b4b2c813
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDispatchEx::InvokeEx
提供對 `IDispatchEx` 物件公開的屬性和方法。  
  
## 語法  
  
```  
HRESULT InvokeEx(  
   DISPID id,  
   LCID lcid,  
   WORD wFlags,  
   DISPARAMS *pdp,  
   VARIANT *pVarRes,   
   EXCEPINFO *pei,   
   IServiceProvider *pspCaller   
);  
```  
  
#### 參數  
 `id`  
 辨識成員。  使用 `GetDispID` 或 `GetNextDispID` 取得分派識別項。  
  
 `lcid`  
 地區設定內容，用於解譯引數。  `lcid` 傳遞至 `InvokeEx` 允許物件解譯其引數特有的地區設定。  
  
 `wFlags`  
 `wFlags` 的合法值為:  
  
 DISPATCH\_PROPERTYGET&#124;DISPATCH\_METHOD&#124;DISPATCH\_PROPERTYPUT&#124;DISPATCH\_PROPERTYPUTREF&#124;DISPATCH\_CONSTRUCT  
  
 描述 `InvokeEx` 呼叫之內容的旗標:  
  
|值|意義|  
|-------|--------|  
|DISPATCH\_METHOD|這個成員做為叫用方法。  如果屬性具有相同的名稱，這個，並 DISPATCH\_PROPERTYGET 旗標可設定 \(定義 `IDispatch`\)。|  
|DISPATCH\_PROPERTYGET|這個成員擷取當做屬性或資料成員 \(定義 `IDispatch`\)。|  
|DISPATCH\_PROPERTYPUT|這個成員變更為屬性或資料成員 \(定義 `IDispatch`\)。|  
|DISPATCH\_PROPERTYPUTREF|參考指派 \(Assignment\) 變更成員而不是值的指派。  這個旗標，則只有在屬性接受物件時的參考 \(定義 `IDispatch`\)。|  
|DISPATCH\_CONSTRUCT|這個成員會當做建構函式。  \(這是 `IDispatchEx`定義新的值\)。  `wFlags` 的合法值為:<br /><br /> DISPATCH\_PROPERTYGET DISPATCH\_METHOD DISPATCH\_PROPERTYPUT DISPATCH\_PROPERTYPUTREF DISPATCH\_CONSTRUCT|  
  
 `pdp`  
 結構的指標，此結構包含引數陣列、指名引數之 DISPID 引數的陣列，以及陣列中元素數目的計數。  提供 DISPPARAMS 結構的完整說明請參閱 `IDispatch` 文件。  
  
 `pVarRes`  
 至結果是儲存位置的指標或空白，如果呼叫端無法預期的結果。  如果 DISPATCH\_PROPERTYPUT 或 DISPATCH\_PROPERTYPUTREF，指定這個引數會被忽略。  
  
 `pei`  
 包含例外狀況資訊的結構指標。  如果傳回， `DISP_E_EXCEPTION` ，應填入這個結構。  可以是空白。  提供 `EXCEPINFO` 結構的完整說明請參閱 `IDispatch` 文件。  
  
 `pspCaller`  
 為呼叫端提供的服務提供者物件的指標，其允許物件從呼叫端的服務。  可以是空白。  
  
 `IDispatchEx::InvokeEx` 提供所有功能 `IDispatch::Invoke` 並將一些副檔名:  
  
|||  
|-|-|  
|DISPATCH\_CONSTRUCT|指出項目會當做建構函式。|  
|`pspCaller`|`pspCaller` 允許呼叫端提供的服務物件的存取。  特定服務可能由呼叫端處理或委派的呼叫端進一步呼叫鏈結。  例如，在中，如果在瀏覽器中指令碼引擎進行 `InvokeEx` 呼叫外部物件，物件可以跟隨 `pspCaller` 鏈結從指令碼引擎或瀏覽器的服務。  \(請注意呼叫鏈結與稱為容器鏈結或網站鏈結的撰寫鏈結也。  撰寫鏈結會透過某種其他機制 \(例如 `IObjectWithSite`\)。|  
|`this` 指標|當 DISPATCH\_METHOD 在 `wFlags`時設定，可能會有一個名為「參數」「this」的值。  物件會 DISPID\_THIS，並且必須是第一個具名參數。|  
  
 移除在 `IDispatch::Invoke` 中未使用的 `riid` 參數。  
  
 移除在 `IDispatch::Invoke` 的 `puArgArr` 參數。  
  
 在下列範例 `IDispatch::Invoke` 參閱文件:  
  
 「呼叫方法沒有任何引數」  
  
 「取得和設定屬性」  
  
 「傳遞參數」。  
  
 「索引屬性」  
  
 「引發例外狀況在期間叫用」  
  
 傳回「false」  
  
## 傳回值  
 下列值的傳回一個值:  
  
|||  
|-|-|  
|`S_OK`|成功。|  
|DISP\_E\_BADPARAMCOUNT|項目數目提供給 DISPPARAMS 與方法或屬性接受的引數數目不同。|  
|DISP\_E\_BADVARTYPE|其中一個 `rgvarg` 的引數不是有效的不同型別。|  
|DISP\_E\_EXCEPTION|應用程式需要引發例外狀況。  在這種情況下，應填入在 `pei` 傳入的結構。|  
|DISP\_E\_MEMBERNOTFOUND|這個要求的成員存在，則為 `InvokeEx` 的呼叫會嘗試設定唯讀屬性的值。|  
|DISP\_E\_NONAMEDARGS|`IDispatch` 的這個實作不支援具名引數。|  
|DISP\_E\_OVERFLOW|其中一個 `rgvarg` 的引數不可以強制轉型為指定的型別。|  
|DISP\_E\_PARAMNOTFOUND|一個參數 DISPID 未對應到方法的參數。|  
|DISP\_E\_TYPEMISMATCH|一個或多個引數不可以強制轉型為。|  
|DISP\_E\_UNKNOWNLCID|成員叫用會依據 LCID 解譯字串引數， LCID，而且無法辨識。  如果不需要 LCID 來解譯引數，應該不會傳回這個錯誤。|  
|DISP\_E\_PARAMNOTOPTIONAL|遺漏必要參數。|  
  
## 範例  
  
```  
VARIANT var;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
   DISPPARAMS dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)))  
   {  
      pdex->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
   }  
```  
  
## 請參閱  
 [IDispatchEx 介面](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx::GetDispID](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)