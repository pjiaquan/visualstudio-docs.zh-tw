---
title: "m_stateFlags 欄位 | Microsoft Docs"
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
  - "m_stateFlags] 欄位中，工作類別 [.NET Framework 偵錯引擎]"
ms.assetid: 82b20efc-08f2-4cd2-91f6-4e01e3da906b
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# m_stateFlags 欄位
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

儲存的目前狀態的相關資訊 <xref:System.Threading.Tasks.Task> 物件。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件︰** mscorlib （在 mscorlib.dll\)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 \(CIL\)。  
  
## 語法  
  
```  
.field assembly int32 modreq(System.Runtime.CompilerServices.IsVolatile) m_stateFlags  
```  
  
## 備註  
 您通常會使用 <xref:System.Threading.Tasks.Task.Status%2A?displayProperty=fullName> 屬性來存取此值。  
  
 這個成員可以是下列值的任何組合︰  
  
-   [TASK\_STATE\_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)  
  
-   [TASK\_STATE\_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)  
  
-   [TASK\_STATE\_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)  
  
-   [TASK\_STATE\_WAITING\_ON\_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)  
  
-   [TASK\_STATE\_RAN\_TO\_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)  
  
## 請參閱  
 [工作類別](../../extensibility/debugger/task-class-internal-members.md)