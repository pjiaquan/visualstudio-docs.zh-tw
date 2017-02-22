---
title: "符號提供者介面 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "介面，符號處理常式"
  - "符號處理常式介面"
  - "符號處理常式中，評估變數"
ms.assetid: 4201f10e-c9f7-4b38-bb45-40fe0082d5bf
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 符號提供者介面
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

以下是符號所處理的介面的[!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]。  
  
## 討論  
 這些介面用來在中斷模式期間評估呼叫堆疊中的變數。  它們會實作僅供通用語言執行階段提供符號者 \(預存程序\)。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)|預存程序|表示某個項目的位址。|  
|[IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)|預存程序|表示位址的項目，提供存取的處理序 id。|  
|[IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)|預存程序|代表陣列中的符號或陣列型別。|  
|[IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)|預存程序|代表類別的符號或類別型別。|  
|[IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md)|預存程序|使用專屬於 managed 程式碼的方法表示 COM \+ 符號提供者。|  
|[IDebugComPlusSymbolProvider2](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2.md)|預存程序|使用專屬於 managed 程式碼的方法表示 COM \+ 符號提供者，並擴充 **IDebugComPlusSymbolProvider**。|  
|[IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)|預存程序|代表符號或其他符號或型別是容器的型別。|  
|[IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)|預存程序|代表自訂屬性可以附加至一個符號。|  
|[IDebugCustomAttributeQuery](../../../extensibility/debugger/reference/idebugcustomattributequery.md)|預存程序|表示方法或型別上的自訂屬性的查詢。|  
|[IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)|預存程序|提供符號自訂屬性的存取。|  
|[IDebugDynamicField](../../../extensibility/debugger/reference/idebugdynamicfield.md)|預存程序|任何型別，可以在執行階段決定基底介面。|  
|[IDebugDynamicFieldCOMPlus](../../../extensibility/debugger/reference/idebugdynamicfieldcomplus.md)|預存程序|此物件代表的動態欄位[IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)物件。|  
|[IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)|預存程序|表示列舉型別。|  
|[IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)|預存程序|延伸 \[可用的欄位，以支援 managed 程式碼的泛用型的別。|  
|[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)|預存程序|基底類別的所有欄位。 代表符號或型別的描述。|  
|[IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)|預存程序|代表欄位的 managed 程式碼的泛型型別定義。|  
|[IDebugGenericFieldInstance](../../../extensibility/debugger/reference/idebuggenericfieldinstance.md)|預存程序|代表欄位的 managed 程式碼的泛型型別執行個體。|  
|[IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)|預存程序|表示為 managed 程式碼的泛型型別參數。|  
|[IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)|預存程序|表示方法。|  
|[IDebugModOpt](../../../extensibility/debugger/reference/idebugmodopt.md)|預存程序|表示偵錯的選擇性修飾詞。|  
|[IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)|預存程序|代表變數的指標。|  
|[IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)|預存程序|表示從基本型別列舉值[IDebugField](../../../extensibility/debugger/reference/idebugfield.md)介面。|  
|[IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)|預存程序|代表可取得或設定的 managed 程式碼類別的屬性。|  
|[IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)|預存程序|代表符號提供者所提供的符號和型別。|  
|[IDebugSymbolProviderDirect](../../../extensibility/debugger/reference/idebugsymbolproviderdirect.md)|預存程序|表示中繼資料和核心符號介面直接存取的符號提供者。|  
|[IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md)|預存程序|代表能夠建立欄位，以表示型別。|  
|[IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)|預存程序|延伸 **IDebugTypeFieldBuilder** ，才能建立陣列型別。|  
|[IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)|預存程序|表示 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) 物件的集合。|  
|[IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)|預存程序|表示 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) 物件的集合。|  
|[IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)|預存程序|表示 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) 物件的集合。|  
  
## 請參閱  
 [應用程式開發介面參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)