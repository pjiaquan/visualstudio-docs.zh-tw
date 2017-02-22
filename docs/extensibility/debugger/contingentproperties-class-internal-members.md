---
title: "ContingentProperties 類別-內部成員 | Microsoft Docs"
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
  - "ContingentProperties 類別 [.NET Framework 偵錯引擎]"
  - "偵錯引擎，ContingentProperties 類別 [.NET Framework]"
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# ContingentProperties 類別-內部成員
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

包含的其他屬性 <xref:System.Threading.Tasks.Task> 物件。  
  
 **命名空間︰** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **組件︰** mscorlib （在 mscorlib.dll\)  
  
 因為您無法從.NET Framework 來存取這些內部成員，下列語法提供通用中繼語言 \(CIL\)。  
  
## 語法  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## 成員  
  
### 欄位  
  
|名稱|描述|  
|--------|--------|  
|[m\_children](../../extensibility/debugger/m-children-field.md)|註冊這項工作的子工作的清單。|  
  
## 備註  
 .NET Framework 初始化這個類別的欄位，只在需要時才。  
  
## 請參閱  
 [.NET Framework 的平行擴充內部](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)