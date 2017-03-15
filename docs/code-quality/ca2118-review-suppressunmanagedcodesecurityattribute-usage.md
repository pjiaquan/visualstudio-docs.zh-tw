---
title: "CA2118：必須檢視 SuppressUnmanagedCodeSecurityAttribute 使用方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
helpviewer_keywords: 
  - "CA2118"
  - "ReviewSuppressUnmanagedCodeSecurityUsage"
ms.assetid: 4cb8d2fc-4e44-4dc3-9b74-7f5838827d41
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2118：必須檢視 SuppressUnmanagedCodeSecurityAttribute 使用方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|ReviewSuppressUnmanagedCodeSecurityUsage|  
|CheckId|CA2118|  
|分類|Microsoft.Security|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的型別或成員具有 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> 屬性 \(Attribute\)。  
  
## 規則描述  
 對於使用 COM Interop 或平台引動過程執行 Unmanaged 程式碼的成員，<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 會變更安全性系統的預設行為。  通常，系統會針對 Unmanaged 程式碼的權限進行[資料與模型化](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)。  每次引動成員時，這個要求會發生於執行階段，並檢查呼叫堆疊中的每一個呼叫端是否具有使用權限。  當屬性存在時，系統會針對使用權限進行[Link Demands](../Topic/Link%20Demands.md)：當呼叫端是以 JIT 編譯時，會檢查立即呼叫端的使用權限。  
  
 這個屬性主要是用於增加效能，不過，效能提升會伴隨顯著的安全性風險。  如果您將屬性置於呼叫原生 \(Native\) 方法的 public 成員，則呼叫堆疊中的呼叫端 \(不是立即呼叫端\) 不需要 Unmanaged 程式碼權限，即可執行 Unmanaged 程式碼。  根據 public 成員的動作及輸入處理，它可能允許不可信賴的呼叫端存取一般限制為可信賴程式碼的功能。  
  
 [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 會依賴安全性檢查，以防止呼叫端直接存取目前處理序 \(Process\) 的位址空間。  因為這個屬性會略過一般安全性，所以如果您的程式碼可以用於讀取或寫入處程序的記憶體，則它會引起嚴重的威脅。  請注意，風險不限於有意提供處理序記憶體存取權的方法。風險也會出現在惡意程式碼可以透過任何方法達成存取的任何案例中，例如，透過意外、不正確或無效的輸入。  
  
 除非組件 \(Assembly\) 是從本機電腦執行，或是下列其中一個群組的成員，否則預設的安全性原則不會將 Unmanaged 程式碼權限授與組件：  
  
-   My Computer Zone 程式碼群組  
  
-   Microsoft 強式名稱 \(Strong Name\) 程式碼群組  
  
-   ECMA 強式名稱程式碼群組  
  
## 如何修正違規  
 仔細檢閱程式碼，以確定這個屬性是絕對必要的。  如果您不熟悉 Managed 程式碼安全性，或不了解使用這個屬性的安全性含意，請從程式碼中移除它。  如果需要此屬性，則必須確定呼叫端無法惡意地使用程式碼。  如果程式碼沒有執行 Unmanaged 程式碼的使用權限，則這個屬性不會有任何作用，因此應該將屬性移除。  
  
## 隱藏警告的時機  
 若要放心地隱藏這項規則的警告，您必須確定程式碼不會提供呼叫端存取原生作業或資源的權限，因為這種存取權限可能會遭到惡意使用。  
  
## 範例  
 下列範例會違反這項規則。  
  
 [!code-cs[FxCop.Security.TypesDoNotSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_1.cs)]  
  
## 範例  
 在下列範例中，`DoWork` 方法會提供平台引動方法 \(Platform Invocation Method\) `FormatHardDisk` 的可公開存取程式碼路徑。  
  
 [!code-cs[FxCop.Security.PInvokeAndSuppress#1](../code-quality/codesnippet/CSharp/ca2118-review-suppressunmanagedcodesecurityattribute-usage_2.cs)]  
  
## 範例  
 在下列範例中，public 方法 `DoDangerousThing` 會導致違規。  若要解決此違規，應將 `DoDangerousThing` 變成私用 \(Private\)，並透過安全性要求所保護的 public 方法存取它，如同 `DoWork` 方法中所述。  
  
 [!CODE [FxCop.Security.TypeInvokeAndSuppress#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Security.TypeInvokeAndSuppress#1)]  
  
## 請參閱  
 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName>   
 [Secure Coding Guidelines](../Topic/Secure%20Coding%20Guidelines.md)   
 [Security Optimizations](http://msdn.microsoft.com/zh-tw/cf255069-d85d-4de3-914a-e4625215a7c0)   
 [資料與模型化](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)   
 [Link Demands](../Topic/Link%20Demands.md)