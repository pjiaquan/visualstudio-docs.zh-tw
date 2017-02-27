---
title: "m_children 欄位 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "m_children 欄位 ContingentProperties 類別 [.NET Framework 偵錯引擎]"
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# m_children 欄位
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

註冊這項工作的子工作的清單。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件︰** mscorlib （在 mscorlib.dll\)  
  
 因為您無法從.NET Framework 來存取這個內部成員，下列語法提供通用中繼語言 \(CIL\)。  
  
## 語法  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## 備註  
 執行工作時，會執行工作的執行緒應該存取這個陣列。  
  
 如果工作已完成，其他執行緒可以存取這個欄位，只要它們不加入任何項目，或從中移除任何項目。  
  
## 請參閱  
 [ContingentProperties 類別](../../extensibility/debugger/contingentproperties-class-internal-members.md)