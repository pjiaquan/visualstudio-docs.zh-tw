---
title: "IActiveScriptStringCompare::StrComp | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStringCompare.StrComp
apilocation: scrobj.dll
helpviewer_keywords: 
  - "StrComp 方法, IActiveScriptStringCompare 介面"
ms.assetid: 124d1281-8037-4766-a2a1-61244ac1f114
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStringCompare::StrComp
定義指令碼引擎的字串比較方法。  
  
## 語法  
  
```  
HRESULT StrComp(  
// The first string:  
    [in] BSTR bszStr1,    
// The second string:   
    [in] BSTR bszStr2,    
// The result of the comparison:  
    [out, retval] LONG* iRet   
);  
```  
  
#### 參數  
 `bszStr1`  
 第一個字串。  
  
 `bszStr2`  
 第二個字串。  
  
 `iRet`  
 比較的結果。  如果為 0，則 `bszStr1` 和 `bszStr2`相同，如果為 \-1，則 `bszStr1` \< `bszStr2`;如果為 1，則 `bszStr1` \> `bszStr2`。  
  
## 傳回值  
 下列值的傳回一個值:  
  
|傳回值|意義|  
|---------|--------|  
|`S_OK`|成功。|  
|`E_INVALIDARG`|引數是無效的。|  
|`E_UNEXPECTED`|這個呼叫不需要 \(例如，指令碼引擎尚未載入或未初始化\)。|  
  
## 備註  
 這個方法會在每次呼叫字串比較實作。  
  
## 範例  
 下列範例說明如何多載字串比較函式。  因此，使用 [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) 設定 SCRIPTPROP\_STRINGCOMPAREINSTANCE 時，多載允許。  
  
```cpp#  
cpp_quote("// {58562769-ED52-42f7-8403-4963514E1F11}")  
cpp_quote("DEFINE_GUID(IID_IActiveScriptStringCompare, 0x58562769,   
    0xED52, 0x42f7, 0x84, 0x03, 0x49, 0x63, 0x51, 0x4E, 0x1F, 0x11);")  
cpp_quote("")  
  
cpp_quote("#define SCRIPTPROP_INTEGERMODE              0x00003000")  
cpp_quote("#define SCRIPTPROP_STRINGCOMPAREINSTANCE    0x00003001")  
cpp_quote("")  
interface IActiveScriptStringCompare;  
[  
         object,  
         uuid(58562769-ED52-42f7-8403-4963514E1F11),  
         pointer_default(unique)  
]  
interface IActiveScriptStringCompare : IUnknown  
{  
        // StrComp  
        //     bszStr1: first string  
        //     bszStr2: second string  
        //     iRet: 0 if identical, -1 if bszStr1 < bszStr2, 1 if   
        //         bszStr1 > bszStr2  
        //            
        //     Return values:  
        //         S_OK: Success  
        //         E_NOTIMPL: Not implemented  
        //  
        HRESULT StrComp(  
                [in] BSTR bszStr1,  
                [in] BSTR bszStr2,  
                [out, retval] LONG* iRet  
        );  
}  
```  
  
## 請參閱  
 [IActiveScriptStringCompare 介面](../../winscript/reference/iactivescriptstringcompare-interface.md)