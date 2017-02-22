---
title: "CA2144：透明程式碼不可以從位元組陣列載入組件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2144"
ms.assetid: 777b1310-6e16-4413-b4ee-5f3136304f82
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2144：透明程式碼不可以從位元組陣列載入組件
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|TransparentMethodsShouldNotLoadAssembliesFromByteArrays|  
|CheckId|CA2144|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 透明方法會使用下列其中一種方法從位元組陣列載入組件：  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
-   <xref:System.Reflection.Assembly.Load%2A>  
  
## 規則描述  
 透明程式碼的安全性檢閱不如關鍵性程式碼的安全性檢閱徹底，因為透明程式碼無法執行安全性敏感動作。  透明程式碼中可能不會注意到從位元組陣列載入的組件，而該位元組陣列可能包含需要稽核之重大或更重要的安全關鍵性程式碼。  因此，透明的程式碼不應從位元組陣列載入組件。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請在載入組件的方法標記 <xref:System.Security.SecurityCriticalAttribute> 或 <xref:System.Security.SecuritySafeCriticalAttribute> 屬性。  
  
## 隱藏警告的時機  
 請勿隱藏此規則的警告。  
  
## 範例  
 下列程式碼會引發規則，因為透明的方法會從位元組陣列載入組件。  
  
 [!code-cs[FxCop.Security.CA2144.TransparentMethodsShouldNotLoadAssembliesFromByteArrays#1](../code-quality/codesnippet/CSharp/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays_1.cs)]