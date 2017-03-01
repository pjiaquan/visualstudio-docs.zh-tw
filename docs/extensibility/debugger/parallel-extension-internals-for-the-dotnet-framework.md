---
title: ".NET framework 進行平行擴充內部 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debug engines, internals [.NET Framework]
ms.assetid: 93e07cfa-91fa-464c-b866-8bf5570411df
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c679d573bde8352906471b4eded7ccb9051f5959
ms.lasthandoff: 02/22/2017

---
# <a name="parallel-extension-internals-for-the-net-framework"></a>.NET Framework 的平行擴充內部
本章節描述內部的型別、 方法和欄位的類別，可協助您實作自訂的 parallel extensions 到.NET Framework 偵錯工具。  
  
## <a name="in-this-section"></a>本章節內容  
 [工作類別](../../extensibility/debugger/task-class-internal-members.md)  
 描述內部資料成員的<xref:System.Threading.Tasks.Task?displayProperty=fullName>類別。</xref:System.Threading.Tasks.Task?displayProperty=fullName>  
  
 [TaskScheduler 類別](../../extensibility/debugger/taskscheduler-class-internal-members.md)  
 描述內部資料成員的<xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>類別。</xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>  
  
 [ContingentProperties 類別](../../extensibility/debugger/contingentproperties-class-internal-members.md)  
 描述內部資料成員`System.Threading.Tasks.ContingentProperties`類別。  
  
 [AsyncTaskMethodBuilder 結構](../../extensibility/debugger/asynctaskmethodbuilder-structure-internal-members.md)  
 描述內部成員<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>結構。</xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>  
  
 [AsyncTaskMethodBuilder\<TResult > 結構](../../extensibility/debugger/asynctaskmethodbuilder-tresult-structure-internal-members.md)  
 描述內部成員<xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>結構。</xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>  
  
 [AsyncVoidMethodBuilder 結構](../../extensibility/debugger/asyncvoidmethodbuilder-structure-internal-members.md)  
 描述內部成員<xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>結構。</xref:System.Runtime.CompilerServices.AsyncVoidMethodBuilder>  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName></xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 <xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName></xref:System.Threading.Tasks.TaskScheduler?displayProperty=fullName>   
 [Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)   
 [平行程式設計](http://msdn.microsoft.com/Library/4d83c690-ad2d-489e-a2e0-b85b898a672d)
