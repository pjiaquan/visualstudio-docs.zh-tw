---
title: "SOURCE_TEXT_ATTR 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "SOURCE_TEXT_ATTR 的常數"
ms.assetid: 459384b0-1463-4841-a2b3-a993207163bf
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# SOURCE_TEXT_ATTR 列舉
描述原始程式文字單一字元的屬性。  
  
## 語法  
  
```cpp  
enum enum_SOURCE_TEXT_ATTR  
{  
    SOURCETEXT_ATTR_KEYWORD    = 0x0001,  
    SOURCETEXT_ATTR_COMMENT    = 0x0002,  
    SOURCETEXT_ATTR_NONSOURCE    = 0x0004,  
    SOURCETEXT_ATTR_OPERATOR   = 0x0008,  
    SOURCETEXT_ATTR_NUMBER    = 0x0010,  
    SOURCETEXT_ATTR_STRING    = 0x0020,  
    SOURCETEXT_ATTR_FUNCTION_START  = 0x0040  
};  
  
```  
  
## Members  
  
|成員|值|描述|  
|--------|-------|--------|  
|SOURCETEXT\_ATTR\_KEYWORD|0x0001|字元是語言關鍵字，例如 VBScript，關鍵字 `While`的一部分。|  
|SOURCETEXT\_ATTR\_COMMENT|0x0002|字元是註解區塊的一部分。|  
|SOURCETEXT\_ATTR\_NONSOURCE|0x0004|字元不屬於編譯的語言來源文字的一部分。  例如，圍繞指令碼區塊的 HTML。|  
|SOURCETEXT\_ATTR\_OPERATOR|0x0008|字元是語言運算子的一部分。  例如: ，算術運算子 **\+**。|  
|SOURCETEXT\_ATTR\_NUMBER|0x0010|字元與語言和數值常數的一部分。  例如，常數 3.14159。|  
|SOURCETEXT\_ATTR\_STRING|0x0020|字元是語言字串常數的一部分。  例如，字串「Hello World」。|  
|SOURCETEXT\_ATTR\_FUNCTION\_START|0x0040|字元表示函式區塊的開頭。|  
  
## 備註  
 通常， `IDebugDocumentHost::GetScriptTextAttributes`、 `IActiveScriptDebug::GetScriptletTextAttributes`和 `IActiveScriptDebug::GetScriptTextAttributes` 方法傳回的文字屬性，每一個字元，除非:  
  
-   在中，方法可能會傳回 SOURCETEXT\_ATTR\_IDENTIFIER 和 SOURCETEXT\_ATTR\_MEMBERLOOKUP 旗標的情況下， GETATTRTYPE\_DEPSCAN 旗標設定，  
  
-   在中，方法可能會傳回 SOURCETEXT\_ATTR\_THIS 旗標的情況下， GETATTRFLAG\_THIS 旗標設定，  
  
-   在中，方法可能會傳回 SOURCETEXT\_ATTR\_HUMANTEXT 旗標的情況下， GETATTRFLAG\_HUMANTEXT 旗標設定為。  
  
## 請參閱  
 [動態指令碼偵錯工具的常數、列舉和結構](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)