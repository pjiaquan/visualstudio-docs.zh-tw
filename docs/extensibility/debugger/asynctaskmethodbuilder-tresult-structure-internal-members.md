---
title: "AsyncTaskMethodBuilder &lt; TResult &gt; 結構-內部成員 | Microsoft Docs"
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
  - "AsyncTaskMethodBuilder < TResult > 結構 [.NET Framework 偵錯引擎]"
  - "偵錯引擎，AsyncTaskMethodBuilder < TResult > 結構 [.NET Framework]"
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# AsyncTaskMethodBuilder &lt; TResult &gt; 結構-內部成員
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

本主題描述的內部成員 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 類別。 如需此類別的一般資訊，請參閱 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> 參考主題。  
  
 **命名空間:** <xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **組件:** mscorlib \(在 mscorlib.dll\)  
  
 因為您無法從.NET Framework 來存取這些內部成員，下列語法提供通用中繼語言 \(CIL\)。  
  
## 語法  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## 內部成員  
  
|名稱|描述|  
|--------|--------|  
|[ObjectIdForDebugger 屬性](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|取得物件，可用來唯一識別此產生器來偵錯工具。|  
|[m\_task 欄位](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|表示延遲初始化建置工作。|  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [.NET Framework 的平行擴充內部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)