---
title: "IDiaSymbol::get_undecoratedNameEx | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_undecoratedNameEx 方法"
ms.assetid: 579aed0b-c57d-41a1-a94a-3bf665fd4a9d
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IDiaSymbol::get_undecoratedNameEx
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

擷取部分或全部的 C\+\+ 的未裝飾名稱裝飾 \(連結\) 名稱。  
  
## 語法  
  
```cpp#  
HRESULT get_undecoratedNameEx(   
   DWORD undecorateOptions,  
   BSTR* pRetval  
);  
```  
  
#### 參數  
 `undecoratedOptions`  
 \[in\]指定的旗標組合傳回該控制項。  請參閱 \[備註\] 部份的特定值和它們的功用。  
  
 `pRetVal`  
 \[\] out傳回未裝飾的 C\+\+ 名稱裝飾名稱。  
  
## 傳回值  
 如果成功的話，會傳回`S_OK`。 否則，會傳回`S_FALSE`或錯誤代碼。  
  
> [!NOTE]
>  傳回值為`S_FALSE`表示此屬性不適用於該符號。  
  
## 備註  
 `undecorateOptions`可以是下列旗標的組合。  
  
> [!NOTE]
>  旗標名稱未定義在 DIA SDK 中，因此您必須加入程式碼中的宣告，或使用未經處理的值。  
  
|旗標|值|描述|  
|--------|-------|--------|  
|UNDNAME\_COMPLETE|0x0000|啟用完全 undecoration。|  
|UNDNAME\_NO\_LEADING\_UNDERSCORES|0x0001|移除前置底線 Microsoft 擴充關鍵字。|  
|UNDNAME\_NO\_MS\_KEYWORDS|0x0002|停用擴充的 Microsoft 擴充關鍵字。|  
|UNDNAME\_NO\_FUNCTION\_RETURNS|0x0004|停用擴充的主要宣告的傳回型別。|  
|UNDNAME\_NO\_ALLOCATION\_MODEL|0x0008|停用宣告模型的擴充。|  
|UNDNAME\_NO\_ALLOCATION\_LANGUAGE|0x0010|停用宣告語言規範的擴充。|  
|UNDNAME\_RESERVED1|0x0020|保留。|  
|UNDNAME\_RESERVED2|0x0040|保留。|  
|UNDNAME\_NO\_THISTYPE|0x0060|停用所有的修飾詞，在`this`型別。|  
|UNDNAME\_NO\_ACCESS\_SPECIFIERS|0x0080|停用擴充成員的存取規範。|  
|UNDNAME\_NO\_THROW\_SIGNATURES|0x0100|停用擴充"throw\-"的簽章函式和函式的指標。|  
|UNDNAME\_NO\_MEMBER\_TYPE|0x0200|停用擴充的`static`或`virtual`成員。|  
|UNDNAME\_NO\_RETURN\_UDT\_MODEL|0x0400|對 UDT 傳回，請停用 Microsoft 模型的擴充。|  
|UNDNAME\_32\_BIT\_DECODE|0x0800|Undecorates 32 位元的裝飾的名稱。|  
|UNDNAME\_NAME\_ONLY|0x1000|取得名稱的主要宣告; 只會傳回 \[範圍::\] 名稱。  展開 \[範本參數。|  
|UNDNAME\_TYPE\_ONLY|0x2000|輸入是只是型別支援的編碼。 會將委派撰寫抽象的宣告子。|  
|UNDNAME\_HAVE\_PARAMETERS|0x4000|真正的範本參數是可用的。|  
|UNDNAME\_NO\_ECSU|0x8000|抑制列舉\/類別\/結構\/等位。|  
|UNDNAME\_NO\_IDENT\_CHAR\_CHECK|0x10000|抑制檢查有有效的識別項字元。|  
|UNDNAME\_NO\_PTR64|0x20000|不包括在輸出中的 ptr64。|  
  
## 請參閱  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)