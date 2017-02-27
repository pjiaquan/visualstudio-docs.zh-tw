---
title: "IDebugReference2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugReference2"
helpviewer_keywords: 
  - "IDebugReference2 介面"
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugReference2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

這個介面表示堆疊框架屬性或有些其他屬性的參考。  
  
> [!NOTE]
>  `IDebugReference2`保留供未來使用，以及所有它的方法應該會傳回`E_NOTIMPL`。  
  
## 語法  
  
```  
IDebugReference2 : IUnknown  
```  
  
## 實作器注意事項  
 DE 會實作這個介面來代表特定種類的值的參考。  例如，值可以是數值運算式評估，用於顯示記憶體或暫存器和它們的值清單的記憶體內容的結果。  
  
## 呼叫者的備忘稿  
 呼叫[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)以取得這個介面。  [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)與[GetDerivedMostReference](../Topic/IDebugReference2::GetDerivedMostReference.md)也會傳回這個介面。  
  
## 方法 Vtable 順序  
 下表顯示的方法`IDebugReference2`。  
  
|方法|描述|  
|--------|--------|  
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|取得[DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)將告訴您這個參考的結構。|  
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|設定這個參考，從字串的值。|  
|[SetValueAsReference](../Topic/IDebugReference2::SetValueAsReference.md)|設定從另一個參考這個參考的值。|  
|[EnumChildren](../Topic/IDebugReference2::EnumChildren.md)|列舉這個參考的子系。|  
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|取得這個參考的父代。|  
|[GetDerivedMostReference](../Topic/IDebugReference2::GetDerivedMostReference.md)|取得這個參考的最具衍生性的參考。|  
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|取得這個參考所參考的記憶體位元組。|  
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|取得這個參考的記憶體內容。|  
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|取得大小而定，以位元組為單位，此參考中。|  
|[SetReferenceType](../Topic/IDebugReference2::SetReferenceType.md)|設定這個參考型別。|  
|[比較](../../../extensibility/debugger/reference/idebugreference2-compare.md)|比較這個與另一個參考。|  
  
## 備註  
  
> [!NOTE]
>  這種使用方式的 「 屬性 」 不應該混淆與表示類別、 成員變數雖然`IDebugReference2`可表示這類實體。  
  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)表示屬性，而`IDebugReference2`表示屬性時，通常要進行偵錯程式中的物件參考的參考。  
  
 屬性和參考的主要差異是屬性參考具名物件的執行個體，而參考是指命名的執行個體。  比方說，屬性可能會參考由該程式的堆積中物件`"a.b"`。  另一個屬性可能參照到相同的物件，做為`"c.d"`。  指的這個屬性的方法不能`"a.b"`或`"c.d"`在範圍之內。  這個相同的物件的參考是沒有名稱。 物件可以參考，只要該物件的記憶體有效。  
  
 `IDebugProperty2`介面可以視為具有名稱、 類型及地址的值。  `IDebugReference2`，另一方面，可以視為一個型別和地址。  
  
## 需求  
 標頭: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 組件： Microsoft.VisualStudio.Debugger.Interop.dll  
  
## 請參閱  
 [核心介面](../../../extensibility/debugger/reference/core-interfaces.md)   
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)