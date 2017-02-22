---
title: "m_stateObject 欄位 | Microsoft Docs"
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
  - "m_stateObject] 欄位中，工作類別 [.NET Framework 偵錯引擎]"
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# m_stateObject 欄位
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

物件，表示該動作將會使用的資料。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件︰** mscorlib （在 mscorlib.dll\)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 \(CIL\)。  
  
## 語法  
  
```  
.field assembly object m_stateObject  
```  
  
## 備註  
 這是 `state` 中的參數 <xref:System.Threading.Tasks.Task.%23ctor%2A> 建構函式。 它也是支援欄位，如 <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> 屬性。  
  
## 請參閱  
 [工作類別](../../extensibility/debugger/task-class-internal-members.md)