---
title: "適用於 Managed 程式碼的 Managed 建議規則規則集 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d1160f8-4e51-4e70-99cd-82ad10ee7b32
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# 適用於 Managed 程式碼的 Managed 建議規則規則集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用「Microsoft 最小建議規則」規則集，將焦點放在程式碼中最重要的問題，包括潛在的安全性漏洞、應用程式損毀，以及其他重要的邏輯和設計錯誤等等。  您應在任何為專案建立的自訂規則集內包含此規則集。  
  
|規則|描述|  
|--------|--------|  
|[CA1001](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|具有可處置欄位的型別應該是可處置的|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|正確宣告事件處理常式|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|以 AssemblyVersionAttribute 標記組件|  
|[CA1033](../Topic/CA1033:%20Interface%20methods%20should%20be%20callable%20by%20child%20types.md)|介面方法應該要可以由子型別呼叫|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|擁有原生資源的型別應為可處置|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|將 P\/Invokes 移到 NativeMethods 類別|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|不要隱藏基底類別方法|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|必須正確實作 IDisposable|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|不要在非預期的位置中引發例外狀況|  
|[CA1301](../Topic/CA1301:%20Avoid%20duplicate%20accelerators.md)|避免使用重複的快速鍵|  
|[CA1400](../Topic/CA1400:%20P-Invoke%20entry%20points%20should%20exist.md)|P\/Invoke 進入點應該要存在|  
|[CA1401](../Topic/CA1401:%20P-Invokes%20should%20not%20be%20visible.md)|P\/Invokes 不應該為可見的|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|自動配置型別不應該是 COM 可見的|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|必須在 P\/Invoke 之後立即呼叫 GetLastError|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|COM 可見型別的基底型別應該是 COM 可見的|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|應該符合 COM 註冊方法|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|P\/Invokes 必須正確宣告|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|必須移除空的完成項|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|實值型別欄位應該為可移植的|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|P\/Invoke 宣告應該是可移植的|  
|[CA2002](../Topic/CA2002:%20Do%20not%20lock%20on%20objects%20with%20weak%20identity.md)|請勿鎖定具有弱式識別的物件|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|必須檢視 SQL 查詢中是否有安全性弱點|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|必須指定 P\/Invoke 字串引數的封送處理|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|必須檢查實值型別上的宣告式安全性|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|指標不應該為可見的|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|受保護型別不應公開欄位|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|方法安全性應該是型別的超集合|  
|[CA2116](../Topic/CA2116:%20APTCA%20methods%20should%20only%20call%20APTCA%20methods.md)|APTCA 方法應該只呼叫 APTCA 方法|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|APTCA 型別應該只擴充 APTCA 基底型別|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|不要間接公開具有連結要求的方法|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|覆寫連結要求應該與基底相同|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|必須將有弱點的 finally 子句包裝在外層 try 中|  
|[CA2126](../Topic/CA2126:%20Type%20link%20demands%20require%20inheritance%20demands.md)|必須同時具有型別連結要求和繼承要求|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|安全性關鍵型別可能未參與型別等價|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|預設建構函式至少必須和基底型別的預設建構函式一樣關鍵|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|委派必須繫結至透明度一致的方法|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|覆寫基底方法時，方法必須保持一致的透明度|  
|[CA2137](../Topic/CA2137:%20Transparent%20methods%20must%20contain%20only%20verifiable%20IL.md)|透明方法必須只包含可驗證的 IL|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|透明方法不可以使用 SuppressUnmanagedCodeSecurity 屬性呼叫方法|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|透明程式碼不可以參考安全性關鍵項目|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|透明方法不可以滿足 LinkDemand|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|型別至少必須和基底型別與介面一樣關鍵|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|透明的方法不可以使用安全性判斷提示|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|透明方法不可以呼叫機器碼|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|請重新擲回以保存堆疊詳細資料|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|不要多次處置物件|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|必須初始化實值型別的靜態內嵌欄位|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|不要以 WebMethod 標記 Serviced 元件|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|可處置的欄位應該受到處置|  
|[CA2214](../Topic/CA2214:%20Do%20not%20call%20overridable%20methods%20in%20constructors.md)|不要呼叫建構函式中的可覆寫方法|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|可處置型別應該宣告完成項|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|完成項應該呼叫基底類別完成項|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|請實作序列化建構函式|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|覆寫 ValueType.Equals 時必須一併多載等號比較運算子|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|以 STAThread 標記 Windows Form 進入點|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|必須標記所有不可序列化的欄位|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|必須呼叫 ISerializable 型別上的基底類別方法|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|必須以 SerializableAttribute 標記 ISerializable 型別|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|請正確實作序列化方法|  
|[CA2240](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)|必須正確實作 ISerializable|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|必須提供格式化方法的正確引數|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|必須正確地測試 NaN|