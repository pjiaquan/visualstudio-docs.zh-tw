---
title: "AsyncVoidMethodBuilder 結構-內部成員 | Microsoft Docs"
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
  - "偵錯引擎，AsyncVoidMethodBuilder 結構 [.NET Framework]"
  - "AsyncVoidMethodBuilder 結構 [.NET Framework 偵錯引擎]"
ms.assetid: fe2970ab-d4c5-4355-a8e4-772ee0a57178
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# AsyncVoidMethodBuilder 結構-內部成員
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本主題描述的內部成員 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 類別。 如需此類別的一般資訊，請參閱 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder> 參考主題。  
  
 **命名空間:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **組件:** mscorlib \(在 mscorlib.dll\)  
  
 因為您無法從.NET Framework 來存取這些內部成員，下列語法提供通用中繼語言 \(CIL\)。  
  
## 語法  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncVoidMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## 內部成員  
  
|名稱|描述|  
|--------|--------|  
|[ObjectIdForDebugger 屬性](../../extensibility/debugger/asyncvoidmethodbuilder-objectidfordebugger-property.md)|取得物件，可用來唯一識別此產生器來偵錯工具。|  
|[m\_objectIdForDebugger 欄位](../../extensibility/debugger/asyncvoidmethodbuilder-m-objectidfordebugger-field.md)|表示偵錯工具用來唯一識別這個產生器的延遲初始化的物件。|  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>   
 [.NET Framework 的平行擴充內部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)