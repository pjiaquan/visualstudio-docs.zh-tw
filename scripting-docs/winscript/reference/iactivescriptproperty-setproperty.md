---
title: "IActiveScriptProperty::SetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.SetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "SetProperty 方法, IActiveScriptProperty 介面"
ms.assetid: 0ba429c5-04a3-4505-bc5f-69c505dfca91
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# IActiveScriptProperty::SetProperty
設定由參數所指定的屬性。  
  
## 語法  
  
```  
HRESULT SetProperty(  
// The property value:  
    uint dwProperty,    
// Not used:   
    IntPtr pvarIndex,    
// The value of the property:   
    out object pvarValue,    
);  
```  
  
#### 參數  
 `dwProperty`  
 要設定的屬性值。  
  
 `pvarIndex`  
 不適用。  
  
 `pvarValue`  
 屬性的值。  
  
 `dwProperty` 允許的值列在下表中說明。  
  
|常數|值|意義|  
|--------|-------|--------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|在整數模式強制指令碼引擎分割 \(而不是浮點數模式。  預設值是 `False`。|  
|SCRIPTPROP\_STRINGCOMPAREINSTANCE|0x00003001|允許字串比較要取代的指令碼引擎的函式。|  
|SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION|0x70000002|告知指令碼引擎沒有其他指令碼引擎所存在的全域物件。|  
|SCRIPTPROP\_INVOKEVERSIONING|0x00004000|強制指令碼引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 選取一組語言功能的支援。  預設的一組 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 支援的語言功能指令碼引擎將會出現在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 版本的用戶端指令碼引擎的 5.7 設定的語言功能相當於。|  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數是無效的。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎尚未載入或未初始化\)。|  
  
## 備註  
 若要啟用或停用整數除法，請叫用 `SetProperty` 並轉換 `Boolean` 至 `Object`。  根據預設，屬性值是 `False`。  如果設為， `True`分割作業將只會傳回整數。  
  
 若要啟用或停用自訂字串比較，請叫用 `SetProperty` 並傳入 `Object` 值。  您所傳遞的物件必須實作介面 [IActiveScriptStringCompare 介面](../../winscript/reference/iactivescriptstringcompare-interface.md)。  [IActiveScriptStringCompare 介面](../../winscript/reference/iactivescriptstringcompare-interface.md) 介面的 [StrComp](../../winscript/reference/iactivescriptstringcompare-strcomp.md) 方法都會呼叫字串比較函式執行。  
  
 若要選取一組語言功能的支援，在指令碼引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 初始化時，叫用 `SetProperty` 並透過對應的 SCRIPTPROP\_INVOKEVERSIONING 要啟用的語言功能設定的值。  如果這個屬性設為 1 \(SCRIPTLANGUAGEVERSION\_5\_7\)， 可用語言的語言功能是為那些出現在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 版本的用戶端指令碼引擎的 5.7 一樣。  如果設定為 2 \(SCRIPTLANGUAGEVERSION\_5\_8\)， 可用語言的語言功能是出現在 5.7 版的新功能不在 5.8 版中加入的項目。  根據預設，這個屬性設為 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\)，並搭配語言功能相當於出現在 5.7 版中，除非，主應用程式支援不同的預設行為。  例如， Internet Explorer 8 選取到預設由 5.8 版指令碼引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 支援的語言功能，當 Internet Explorer 8 的預設文件模式為「Internet Explorer 8 個標準」模式。  切換至 Internet Explorer 8 文件模式 Internet Explorer 7 個標準模式或變通方式重設指令碼引擎支援的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 存在於 5.7 版指令碼引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 設定的語言功能。  
  
> [!NOTE]
>  SCRIPTPROP\_INVOKEVERSIONING，只有在指令碼引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 初始化時，應該將設定為。  
  
## 範例  
 下列範例顯示如何強制指令碼引擎使用整數除法如何允許多載比較函式。  
  
```csharp  
BMLScriptEngine bmlScriptEngine = new BMLScriptEngine();  
IActiveScriptProperty scriptProperties = bmlScriptEngine as   
    IActiveScriptProperty;  
  
// Force the scripting engine to use integer division.  
Boolean enableIntegerDivision = true;  
Object vtIntegerDivInstance = (Object)enableIntegerDivision;  
                scriptProperties.SetProperty(SCRIPTPROP_INTEGERDIVISION,   
    System.IntPtr.Zero, ref vtIntegerDivInstance);  
  
// Allow overloading of the compare function.  
BMLScriptStringCompare bmlScriptStringCompareInstance = new   
    BMLScriptStringCompare();  
Object vtStrCmpInstance = (Object)bmlScriptStringCompareInstance;  
scriptProperties.SetProperty(SCRIPTPROP_STRCOMPINST,   
    System.IntPtr.Zero, ref vtStrCmpInstance);  
```  
  
## 請參閱  
 [定義文件相容性](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [版本資訊](../../javascript/reference/javascript-version-information.md)