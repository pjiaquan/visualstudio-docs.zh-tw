---
title: "IDispatchEx 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDispatchEx 介面"
  - "IDispatchEx 介面, 關於 IDispatchEx"
ms.assetid: 37a3303f-f78e-4b5b-aac8-b836c92819de
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDispatchEx 介面
`IDispatchEx`， `IDispatch` 介面的擴充功能，以支援適合動態語言 \(如指令碼語言。  本節說明 `IDispatchEx` 介面，在 `IDispatch` 和 `IDispatchEx`之間的差異和副檔名的理由。  預期讀取器熟悉 `IDispatch` 和存取 `IDispatch` 文件的。  
  
## 備註  
 `IDispatch` 為 Microsoft Visual Basic 基本上已開發出。  `IDispatch` 的主要限制在於它假設，物件是靜態的。  換句話說，，因為在執行階段，物件不會變更，型別資訊可完整描述它們在編譯時期。  在指令碼語言中 \(例如 Scripting Edition 的動態執行階段模型 \(VBScript\) 和 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 和物件模型 \(例如動態 HTML 的 Visual Basic 需要更有彈性的介面。  
  
 `IDispatchEx` 所開發提供更動態的晚期繫結語言適用的例如指令碼語言 `IDispatch` 以及一些副檔名的所有服務。  `IDispatchEx` 額外功能。 `IDispatch` 所提供以外的是:  
  
-   將新的成員加入至物件 \(「expando」\) 搭配 `fdexNameEnsure` 旗標的 `GetDispID` 。  
  
-   刪除物件使用 `DeleteMemberByName` 或 `DeleteMemberByDispID`的成員。  
  
-   區分大小寫的分派作業所使用 `fdexNameCaseSensitive` 或 `fdexNameCaseInsensitive`。  
  
-   搜尋具有隱含使用 `fdexNameImplicit`名稱的成員。  
  
-   列舉物件使用 `GetNextDispID`的 DISPID。  
  
-   從 DISPID 對應至項目名稱使用 `GetMemberName`。  
  
-   取得物件成員使用 `GetMemberProperties`屬性。  
  
-   使用 `this` 指標使用 `InvokeEx` 的方法引動過程的 DISPATCH\_METHOD。  
  
-   允許支援命名空間的概念 `GetNameSpaceParent`取得物件所使用的命名空間之父代的瀏覽器。  
  
 支援 `IDispatchEx` 的物件也可以支援回溯相容性 \(Backward Compatibility\) 的 `IDispatch` 。  支援 `IDispatchEx` 物件的動態本質與這些物件 `IDispatch` 介面的幾種影響。  例如， `IDispatch` 假設下列幾點:  
  
-   成員和參數 DISPID 必須保持固定在物件的存留期。  這可讓用戶端一次衍生介面和快取它們以供日後使用。  
  
 因為 `IDispatchEx` 允許成員的加入和刪除，一組有效 DISPID 維持不變。  不過， `IDispatchEx` 要求物件和成員名稱之間的對應維持不變。  如果成員刪除，這表示:  
  
-   無法重複使用 DISPID，直到有相同名稱的成員建立。  
  
-   物件必須維持有效。 `GetNextDispID`。  
  
-   必須由方法它們必須辨認這個成員為已刪除和將傳回適當的錯誤碼的適當地接受任何 DISPID `IDispatch` 或 `IDispatchEx` \(通常 DISP\_E\_MEMBERNOTFOUND 或 S\_FALSE\)。  
  
## 範例  
 在這個 test\(\) 函式的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 程式碼會執行下列動作:  
  
-   藉由呼叫 `Object` 建構函式建立新物件並將指標指派給變數 Obj 的新物件。  
  
-   建立物件中名為的 Elem 新的項目並指派給這個項目的函式的指標貓。  
  
-   呼叫此函式。  因為它會呼叫方法，以 `this` 指標參考物件 Obj。  函式會將新的項目，列，加入至物件。  
  
 完整的 HTML 程式碼為:  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
  
function test()  
{  
   // Construct new object  
   Obj = new Object();  
  
   // Create new element and assign function pointer  
   Obj.Elem = cat;  
  
   // Call Elem method ("this" == Obj)  
   Obj.Elem();  
  
   // Obj.Bar now exists  
}  
test();  
</script>  
</body>  
</html>  
```  
  
 此相同 Web 網頁上的控制項可以取得分派指標至瀏覽器的指令碼引擎。  控制項可以實作函式 test\(\):  
  
```  
<html>  
<body>  
<script type="text/javascript">  
function cat()  
{  
   // Create new element and assign the value 10  
   this.Bar = 10;  
}  
</script>  
<object id="test" <CLASSID="CLSID:9417DB5D-FA2A-11D0-8CB3-00C04FC2B085">>  
</object>  
</body>  
</html>  
```  
  
 從控制項的程式碼，測試，在命令提示字元 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 函式 `test()`相同。  請注意這些分派呼叫的執行 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎及變更引擎的狀態:  
  
-   使用 `GetDispID()`，取得分派指標貓函式。  
  
-   使用 `GetDispID()`，其可分派物件指標函式。  
  
-   可藉由呼叫物件的 `InvokeEx()` 函式建構物件並取得分派指標指向新建構的物件。  
  
-   使用 `fdexNameEnsure` 旗標的 `GetDispID()` ，建立新的項目， Elem，物件中。  
  
-   使用，將 `InvokeEx()`分派指標貓在項目。  
  
-   呼叫分派指標貓當做方法呼叫 `InvokeEx()` 並傳入分派指標至建構的物件做為 `this` 指標。  
  
-   貓方法建立新的項目，列，在目前 `this` 物件。  
  
-   驗證使用 `GetNextDispID()`，新項目，列，在建構的物件建立透過列舉項目。  
  
 測試控制項的程式碼:  
  
```  
   BOOL test(IDispatchEx *pdexScript)  
   {  
      HRESULT hr;  
      VARIANT var;  
      DISPID dispid, putid;  
      BOOL retval = FALSE;  
      BSTR bstrName = NULL;  
      IDispatch   *pdispObj = NULL, *pdispCat = NULL;  
      IDispatchEx *pdexObj = NULL;  
      DISPPARAMS dispparams, dispparamsNoArgs = {NULL, NULL, 0, 0};  
  
      // Get dispatch pointer for "cat"  
      bstrName = SysAllocString(OLESTR("cat"));  
         if (bstrName == NULL) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYGET, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispCat = var.pdispVal;  
  
      // Create object by calling "Object" constructor  
      bstrName = SysAllocString(OLESTR("Object"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexScript->GetDispID(bstrName, 0, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
      hr = pdexScript->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_CONSTRUCT, &dispparamsNoArgs,   
         &var, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
      pdispObj = var.pdispVal;  
      hr = pdispObj->QueryInterface(IID_IDispatchEx, (void **)&pdexObj);  
         if (FAILED(hr)) goto LDone;  
  
      // Create new element in object  
      bstrName = SysAllocString(OLESTR("Elem"));  
         if (NULL == bstrName) goto LDone;  
      hr = pdexObj->GetDispID(bstrName, fdexNameEnsure, &dispid);  
         if (FAILED(hr)) goto LDone;  
      SysFreeString(bstrName);  
         bstrName = NULL;  
  
      // Assign "cat" dispatch pointer to element  
      putid = DISPID_PROPERTYPUT;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispCat;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,   
         DISPATCH_PROPERTYPUTREF, &dispparams,  
         NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Invoke method with "this" pointer  
      putid = DISPID_THIS;  
      var.vt = VT_DISPATCH;  
      var.pdispVal = pdispObj;  
      dispparams.rgvarg = &var;  
      dispparams.rgdispidNamedArgs = &putid;  
      dispparams.cArgs = 1;  
      dispparams.cNamedArgs = 1;  
      hr = pdexObj->InvokeEx(dispid, LOCALE_USER_DEFAULT,  
         DISPATCH_METHOD, &dispparams,  
            NULL, NULL, NULL);  
         if (FAILED(hr)) goto LDone;  
  
      // Confirm that new element "Bar" is in object  
      hr = pdexObj->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
      while (hr == NOERROR)  
      {  
            hr = pdexObj->GetMemberName(dispid, &bstrName);  
            if (FAILED(hr)) goto LDone;  
            retval = !wcscmp(bstrName, OLESTR("Bar"));  
            SysFreeString(bstrName);  
            bstrName = NULL;  
            if (retval) goto LDone;  
         hr = pdexObj->GetNextDispID(fdexEnumAll, dispid, &dispid);  
      }  
LDone:  
   SysFreeString(bstrName);  
   if (pdispCat != NULL)  
      pdispCat->Release();  
   if (pdispObj != NULL)  
      pdispObj->Release();  
   if (pdexObj != NULL)  
      pdexObj->Release();  
  
   return retval;  
   }  
```  
  
## 方法  
 [IDispatchEx 方法](../../winscript/reference/idispatchex-methods.md)