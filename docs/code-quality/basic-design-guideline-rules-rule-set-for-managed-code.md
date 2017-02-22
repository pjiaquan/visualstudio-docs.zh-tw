---
title: "適用於 Managed 程式碼的基本設計方針規則規則集 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7eb384f5-f961-400b-b151-115d92addc6a
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 適用於 Managed 程式碼的基本設計方針規則規則集
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用「Microsoft 基本設計方針規則」規則集，將重點放在讓程式碼更易懂又好用。  如果專案包含程式庫程式碼或您想強制執行最佳做法以便於維護程式碼，則應包含這個規則集。  
  
 「基本設計方針規則」包含「Microsoft 最小建議規則」規則集中的所有規則。  如需最小規則的清單，請參閱 [適用於 Managed 程式碼的 Managed 建議規則規則集](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md)。  
  
 下表說明「Microsoft 基本設計方針規則」規則集中的所有規則。  
  
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
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|不要在泛型型別上宣告靜態成員|  
|[CA1002](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)|不要公開泛型清單|  
|[CA1003](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)|必須使用一般事件處理常式執行個體|  
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|泛型方法應該提供型別參數|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|避免在泛型型別上包含過多參數|  
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|不要在成員簽章中巢狀化泛型型別|  
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|建議在適當時使用泛型|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|列舉值中應該要有值為零的成員|  
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|集合應該實作泛型介面|  
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|建議將基底型別當做參數傳遞|  
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|抽象型別不應具有建構函式|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|多載加號和減號運算子時必須一併多載等號比較運算子|  
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|以 CLSCompliantAttribute 標記組件|  
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|以 ComVisibleAttribute 標記組件|  
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|以 AttributeUsageAttribute 標記屬性|  
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|必須定義屬性引數的存取子|  
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|不應該使用多維索引子|  
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|建議在適當時使用屬性|  
|[CA1025](../Topic/CA1025:%20Replace%20repetitive%20arguments%20with%20params%20array.md)|必須以參數陣列取代重複的引數|  
|[CA1026](../Topic/CA1026:%20Default%20parameters%20should%20not%20be%20used.md)|不應使用預設參數|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|必須以 FlagsAttribute 標記列舉|  
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|列舉儲存區應該是 Int32|  
|[CA1030](../Topic/CA1030:%20Use%20events%20where%20appropriate.md)|建議在適當時使用事件|  
|[CA1031](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)|不要攔截一般例外狀況型別|  
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|必須實作標準例外狀況建構函式|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|巢狀型別不應為可見|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|ICollection 實作包含強型別成員|  
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|必須在 Comparable 型別中覆寫方法|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|列舉程式應該是強型別|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|清單為強型別|  
|[CA1041](../Topic/CA1041:%20Provide%20ObsoleteAttribute%20message.md)|提供 ObsoleteAttribute 訊息|  
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|必須針對索引子使用整數類或字串引數|  
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|屬性不應為唯寫|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|請勿多載參考型別上的等號比較運算子|  
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|密封型別不應該宣告 protected 成員。|  
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|不要在密封型別中宣告 virtual 成員|  
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|在命名空間中宣告型別|  
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|不要宣告可見的執行個體欄位|  
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|靜態預留位置型別應該為密封的|  
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|靜態預留位置型別不應包含建構函式|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|URI 參數不應該為字串|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|URI 傳回值不應該為字串|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|URI 屬性不應該為字串|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|字串 URI 多載呼叫 System.Uri 多載|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|型別不應該擴充特定的基底型別|  
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|成員不應該公開特定的具象型別。|  
|[CA1064](../Topic/CA1064:%20Exceptions%20should%20be%20public.md)|例外狀況必須是公用|  
|[CA1500](../Topic/CA1500:%20Variable%20names%20should%20not%20match%20field%20names.md)|變數名稱不應該與欄位名稱相符|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|避免過度複雜|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|識別項名稱不應該只靠大小寫區別|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|識別項名稱不應該和關鍵字相符|  
|[CA1801](../Topic/CA1801:%20Review%20unused%20parameters.md)|必須檢視未使用的參數|  
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|必須移除未使用的區域變數|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|避免使用過多區域變數|  
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|必須初始化參考型別內部的靜態欄位|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|避免使用未呼叫的私用程式碼|  
|[CA1812](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)|避免使用未執行個體化的內部類別|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|避免使用非密封屬性|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|建議使用不規則陣列取代多維陣列|  
|[CA1815](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)|覆寫實值型別上的等號和等號比較運算子|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|屬性不應傳回陣列|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|應該使用字串長度測試空白字串|  
|[CA1822](../Topic/CA1822:%20Mark%20members%20as%20static.md)|將成員標記為靜態|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|避免包含未使用的私用欄位|  
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|不要引發保留的例外狀況型別|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|必須使用 Win32 API 的 Managed 對應項|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|請正確執行個體化引數例外狀況|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|非常數欄位不應該為可見的|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|不要以 FlagsAttribute 標記列舉|  
|[CA2219](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)|不要在 exception 子句中引發例外狀況|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|完成項應該受到保護|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|請勿降低繼承成員的可視性|  
|[CA2223](../Topic/CA2223:%20Members%20should%20differ%20by%20more%20than%20return%20type.md)|成員不應該只有在傳回型別上不同|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|多載等號比較運算子時必須一併覆寫 Equals|  
|[CA2225](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)|運算子多載必須有具名的替代方法|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|運算子應該有對稱的多載|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|集合屬性應該為唯讀|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|必須使用 params 做為變數引數|  
|[CA2234](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)|必須傳遞 System.Uri 物件，而不要傳遞字串|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|必須為選擇性欄位提供還原序列化方法|