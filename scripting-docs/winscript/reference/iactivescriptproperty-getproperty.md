---
title: "IActiveScriptProperty::GetProperty | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptProperty.GetProperty
apilocation: scrobj.dll
helpviewer_keywords: 
  - "GetProperty 方法, IActiveScriptProperty 介面"
ms.assetid: a43383db-b148-4d76-83bd-4f0e899b7cb1
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# IActiveScriptProperty::GetProperty
取得由參數所指定的屬性。  
  
## 語法  
  
```  
HRESULT GetProperty(  
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
 要取得的屬性值。  
  
 `pvarIndex`  
 不適用。  
  
 `pvarValue`  
 屬性的值。  
  
 `dwProperty` 允許的值列在下表中說明。  
  
|常數|值|意義|  
|--------|-------|--------|  
|SCRIPTPROP\_INTEGERMODE|0x00003000|在整數模式強制指令碼引擎分割 \(而不是浮點數模式。|  
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
 主應用程式可以使用屬性 SCRIPTPROP\_ABBREVIATE\_GLOBALNAME\_RESOLUTION 告知一個指令碼引擎沒有其他指令碼引擎所存在的全域物件。  例如， Internet Explorer 可能會告知 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎所呈現網頁只包含 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 指令碼。  因此，只 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 引擎可將新屬性加入至全域物件視窗中，而且沒有 Scripting Edition \(VBScript\) 引擎的 Visual Basic 是相同的。  引擎會忽略這個旗標或可以使用以最佳化加入全域物件新成員的管理。  
  
 在指令碼引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 啟動時，主應用程式可以使用 SCRIPTPROP\_INVOKEVERSIONING 屬性選取一組語言功能的支援。  如果這個屬性設為 1 \(SCRIPTLANGUAGEVERSION\_5\_7\)， 可用語言的語言功能是為那些出現在 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 版本的用戶端指令碼引擎的 5.7 一樣。  如果設定為 2 \(SCRIPTLANGUAGEVERSION\_5\_8\)，可用語言的語言功能是出現在 5.7 版的功能不在 5.8 版中加入的項目。  根據預設，這個屬性設為 0 \(SCRIPTLANGUAGEVERSION\_DEFAULT\)，並搭配語言功能相當於出現在 5.7 版中，除非，主應用程式支援不同的預設行為。  例如，根據預設，在 Internet Explorer 8 文件的方式為「Internet Explorer 8 個標準模式時， Internet Explorer 8 選取到版本所支援的語言功能 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 5.8 指令碼引擎的 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] 。  
  
## 請參閱  
 [定義文件相容性](http://msdn.microsoft.com/library/cc288325)   
 [IActiveScriptProperty](../../winscript/reference/iactivescriptproperty.md)   
 [版本資訊](../../javascript/reference/javascript-version-information.md)