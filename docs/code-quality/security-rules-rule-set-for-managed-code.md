---
title: "適用於 Managed 程式碼的安全性規則規則集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 適用於 Managed 程式碼的安全性規則規則集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您應包含「Microsoft 安全性規則」規則集，讓回報的潛在安全性問題數目達到最大。  
  
|規則|描述|  
|--------|--------|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|必須檢視 SQL 查詢中是否有安全性弱點|  
|[CA2102](../code-quality/ca2102-catch-non-clscompliant-exceptions-in-general-handlers.md)|在一般處理常式中攔截非 CLSCompliant 的例外狀況|  
|[CA2103](../code-quality/ca2103-review-imperative-security.md)|必須檢視命令式安全性|  
|[CA2104](../code-quality/ca2104-do-not-declare-read-only-mutable-reference-types.md)|不要宣告唯讀的可變動參考型別|  
|[CA2105](../code-quality/ca2105-array-fields-should-not-be-read-only.md)|陣列欄位不應為唯讀|  
|[CA2106](../code-quality/ca2106-secure-asserts.md)|保護判斷提示|  
|[CA2107](../code-quality/ca2107-review-deny-and-permit-only-usage.md)|必須檢視 Deny 和 Permit Only 的使用方式|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|必須檢查實值型別上的宣告式安全性|  
|[CA2109](../code-quality/ca2109-review-visible-event-handlers.md)|必須檢視可見的事件處理常式|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|指標不應該為可見的|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|受保護型別不應公開欄位|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|方法安全性應該是型別的超集合|  
|[CA2115](../Topic/CA2115:%20Call%20GC.KeepAlive%20when%20using%20native%20resources.md)|使用原生資源時必須呼叫 GC.KeepAlive|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|APTCA 方法應該只呼叫 APTCA 方法|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 型別應該只擴充 APTCA 基底型別|  
|[CA2118](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md)|必須檢視 SuppressUnmanagedCodeSecurityAttribute 使用方法|  
|[CA2119](../code-quality/ca2119-seal-methods-that-satisfy-private-interfaces.md)|密封方法以滿足私用介面的要求|  
|[CA2120](../Topic/CA2120:%20Secure%20serialization%20constructors.md)|必須保護序列化建構函式|  
|[CA2121](../Topic/CA2121:%20Static%20constructors%20should%20be%20private.md)|靜態建構函式應為私用|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|不要間接公開具有連結要求的方法|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|覆寫連結要求應該與基底相同|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|必須將有弱點的 finally 子句包裝在外層 try 中|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|必須同時具有型別連結要求和繼承要求|  
|[CA2130](../code-quality/ca2130-security-critical-constants-should-be-transparent.md)|安全性關鍵常數應該是透明的|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|安全性關鍵型別可能未參與型別等價|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|預設建構函式至少必須和基底型別的預設建構函式一樣關鍵|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|委派必須繫結至透明度一致的方法|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|覆寫基底方法時，方法必須保持一致的透明度|  
|[CA2135](../Topic/CA2135:%20Level%202%20assemblies%20should%20not%20contain%20LinkDemands.md)|層級 2 組件不應該包含 LinkDemand|  
|[CA2136](../Topic/CA2136:%20Members%20should%20not%20have%20conflicting%20transparency%20annotations.md)|成員不應該具有衝突的透明度附註|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|透明方法必須只包含可驗證的 IL|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法|  
|[CA2139](../Topic/CA2139:%20Transparent%20methods%20may%20not%20use%20the%20HandleProcessCorruptingExceptions%20attribute.md)|透明方法不能使用 HandleProcessCorruptingExceptions 屬性|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透明程式碼不可以參考安全性關鍵項目|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透明方法不可以滿足 LinkDemand|  
|[CA2142](../code-quality/ca2142-transparent-code-should-not-be-protected-with-linkdemands.md)|透明程式碼不可以使用 LinkDemand 加以保護|  
|[CA2143](../Topic/CA2143:%20Transparent%20methods%20should%20not%20use%20security%20demands.md)|透明方法不可以使用安全性要求|  
|[CA2144](../code-quality/ca2144-transparent-code-should-not-load-assemblies-from-byte-arrays.md)|透明程式碼不可以從位元組陣列載入組件|  
|[CA2145](../code-quality/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurityAttribute 來裝飾|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|型別至少必須和基底型別與介面一樣關鍵|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透明的方法不可以使用安全性判斷提示|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透明方法不可以呼叫機器碼|  
|[CA2210](../Topic/CA2210:%20Assemblies%20should%20have%20valid%20strong%20names.md)|組件應包含有效的強式名稱|