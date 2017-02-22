---
title: "設計警告 | Microsoft Docs"
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
  - "vs.codeanalysis.designrules"
helpviewer_keywords: 
  - "設計警告"
  - "Managed 程式碼分析警告, 設計警告"
  - "警告, 設計"
ms.assetid: 34e65a18-560c-423f-814f-519089e318cf
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 設計警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

設計警告支援會遵循 .NET Framework 設計方針。  
  
## 在本節中  
  
|規則|說明|  
|--------|--------|  
|[CA1000：不要在泛型類型上宣告靜態成員](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|呼叫泛型型別的靜態成員時，必須為型別指定型別引數。  呼叫不支援介面的泛型執行個體 \(Instance\) 成員時，必須為成員指定型別引數。  在上述兩種情況下，指定型別引數的語法不同且容易混淆。|  
|[CA1001：具有可處置欄位的類型應該是可處置的](../Topic/CA1001:%20Types%20that%20own%20disposable%20fields%20should%20be%20disposable.md)|類別會宣告及實作型別為 System.IDisposable 的執行個體欄位，且該類別不會實作 IDisposable。  宣告 IDisposable 欄位的類別會間接擁有 Unmanaged 資源，且應實作 IDisposable 介面。|  
|[CA1002：不要公開泛型清單](../Topic/CA1002:%20Do%20not%20expose%20generic%20lists.md)|System.Collections.Generic.List\<\(Of \<\(T\>\)\>\) 是專為效能而非繼承所設計的泛型集合。  因此，List 不包含任何虛擬成員。  應該改為公開專為繼承所設計的泛型集合。|  
|[CA1003：必須使用一般事件處理常式執行個體](../Topic/CA1003:%20Use%20generic%20event%20handler%20instances.md)|型別包含會傳回 void 的委派 \(Delegate\)，其簽章 \(Signature\) 包含兩個參數 \(第一個參數是物件，第二個參數則是可指派給 EventArgs 的型別\)，而包含組件 \(Assembly\) 則會以 [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)] 為目標。|  
|[CA1004：泛型方法應該提供類型參數](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|推斷是指如何利用傳遞到泛型方法的引數型別，而不是利用型別引數的明確規格，來決定泛型方法的型別引數。  若要啟用推斷，泛型方法的參數簽章必須包含與方法之型別參數具有相同型別的參數。  在上述情形中，不必指定型別引數。  當您使用所有型別參數的推斷時，呼叫泛型和非泛型執行個體方法之語法是相同的。這簡化泛型方法的可用性。|  
|[CA1005：避免在泛型類型上包含過多參數](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|泛型型別所包含的型別參數越多，就越難了解並記住每個型別參數所代表的含意。  若是只包含一種型別參數 \(如 List\<T\>\)，以及包含兩個型別參數的某些特定情況 \(如 Dictionary\<TKey, TValue\>\)，這些通常都清楚易懂。  不過，如果存在兩個以上的型別參數，則對大多數使用者而言都會變得難以理解。|  
|[CA1006：不要在成員簽章中巢狀化泛型類型](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|巢狀型別引數就是也是泛型型別的型別引數。  若要呼叫其簽章含有巢狀型別引數的成員，則使用者必須具現化 \(Instantiate\) 一個泛型型別，並將這個型別傳遞給第二個泛型型別的建構函式。  必要程序及語法十分複雜，且應予以避免。|  
|[CA1007：建議在適當時使用泛型](../code-quality/ca1007-use-generics-where-appropriate.md)|外部可見的方法包含 System.Object 型別的參考參數。  使用泛型方法可讓所有型別 \(遵守條件約束\) 傳遞給方法，而不需要先將型別轉型為參考參數型別。|  
|[CA1008：列舉值中應該要有值為零的成員](../code-quality/ca1008-enums-should-have-zero-value.md)|如同其他實值型別一般，未初始化的列舉其預設值為零。  非旗標屬性的列舉應該要使用零值來定義成員，讓預設值成為列舉的有效值。  如果已套用 FlagsAttribute 屬性的列舉定義零值成員，則其名稱應該是 "None"，以表示列舉中未設定任何值。|  
|[CA1009：正確宣告事件處理常式](../code-quality/ca1009-declare-event-handlers-correctly.md)|事件處理常式方法會採用兩個參數。  第一個的型別為 System.Object 且名稱為 "sender"。  這是引發事件的物件。  第二個參數的型別為 System.EventArgs 且名稱為 "e"。  這是與事件相關聯的資料。  事件處理常式方法不應該傳回值；在 C\# 程式設計語言中，這是由 void 傳回型別所表示。|  
|[CA1010：集合應該實作泛型介面](../code-quality/ca1010-collections-should-implement-generic-interface.md)|若要放寬集合的可用性，請實作其中一個泛型集合介面。  接著，使用該集合填入泛型集合型別。|  
|[CA1011：建議將基底類型當做參數傳遞](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|當方法宣告將基底型別指定為參數，則從此基底型別衍生的任何型別都可以當做對應引數傳遞給方法。  如果不需要以衍生參數型別提供額外的功能，則使用基底型別可以更廣泛地運用此方法。|  
|[CA1012：抽象類型不應具有建構函式](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|只有衍生型別 \(Derived Type\) 可以呼叫抽象型別上的建構函式。  因為公用建構函式會建立型別的執行個體，而且您無法建立抽象型別的執行個體，因此具有公用建構函式的抽象型別設計不正確。|  
|[CA1013：多載加號和減號運算子時必須一併多載等號比較運算子](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|公用或保護的型別會實作加法或減法運算，但不會實作等號比較運算子。|  
|[CA1014：以 CLSCompliantAttribute 標記組件](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Common Language Specification \(CLS\) 會定義命名限制、資料型別及組件必須遵守的規則 \(如果組件會使用於跨程式設計語言時\)。  良好的設計會要求所有組件使用 CLSCompliantAttribute 明確表示 CLS 符合性。  如果這個屬性未出現於組件中，則表示組件不符合標準。|  
|[CA1016：以 AssemblyVersionAttribute 標記組件](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|.NET Framework 會使用版本號碼以便唯一識別組件，並繫結至強式名稱組件中的型別。  版本號碼會與版本和發行者 \(Publisher\) 原則一起使用。  應用程式預設只會與建置它們的組件版本一起執行。|  
|[CA1017：以 ComVisibleAttribute 標記組件](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|ComVisibleAttribute 會判斷 COM 用戶端如何存取 Managed 程式碼。  良好的設計會要求組件明確表示 COM 的可視性。  COM 的可視性可以針對整個組件進行設定，然後針對個別型別及型別成員進行覆寫。  如果這個屬性不存在，則 COM 用戶端可以看到組件的內容。|  
|[CA1018：以 AttributeUsageAttribute 標記屬性](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|當您定義自訂屬性時，請使用 AttributeUsageAttribute 標記它，以指出可以在原始程式碼的哪個位置套用自訂屬性。  屬性的意義和預期的用法將決定它在程式碼中的有效位置。|  
|[CA1019：必須定義屬性引數的存取子](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|屬性可以定義必須在將屬性套用至目標時指定的強制引數。  這些引數也稱為位置引數，因為它們會當做位置參數提供給屬性建構函式。  對於每個強制引數而言，屬性 \(Attribute\) 還須提供對應的唯讀屬性 \(Property\)，才可以在執行時期擷取引數值。  屬性也可以定義選擇性引數，也稱為具名引數。  這些引數會依照名稱提供給屬性 \(Attribute\) 建構函式，且必須有對應的讀取\/寫入屬性 \(Property\)。|  
|[CA1020：避免在命名空間中包含過少的類型](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|請確定每個命名空間都有邏輯組織，而且您有合理的理由可以將型別置於沒有嚴密填入的命名空間中。|  
|[CA1021：避免使用 out 參數](../code-quality/ca1021-avoid-out-parameters.md)|以傳址方式傳遞型別時 \(使用 out 或 ref\)，您需要擁有使用指標的經驗、了解實值型別和參考型別之間的差異，並處理具有多個傳回值的方法。  此外，out 和 ref 參數之間的差異一般人不甚了解。|  
|[CA1023：不應該使用多維索引子](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|索引子 \(也就是索引屬性\) 應使用單一索引。  多維索引子會大幅降低程式庫的可用性。|  
|[CA1024：建議在適當時使用屬性](../code-quality/ca1024-use-properties-where-appropriate.md)|公用或保護的方法具有以 "Get" 開頭的名稱，該名稱不採用任何參數並且會傳回不是陣列的值。  此方法可能是成為屬性的不錯候選者。|  
|[CA1025：必須以參數陣列取代重複的引數](../Topic/CA1025:%20Replace%20repetitive%20arguments%20with%20params%20array.md)|當引數的正確數目未知，而且變數引數都是相同的型別 \(或可以相同的型別傳遞\) 時，需使用參數陣列而不是重複的引數。|  
|[CA1026：不應使用預設參數](../Topic/CA1026:%20Default%20parameters%20should%20not%20be%20used.md)|允許使用預設參數的方法受制於 CLS。不過，CLS 允許編譯器 \(Compiler\) 忽略已指派給這些參數的值。  若要在程式語言之間維護您要的行為，則必須以提供預設參數的方法多載來取代使用預設參數的方法。|  
|[CA1027：必須以 FlagsAttribute 標記列舉](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|列舉型別是一種實值型別 \(Value Type\)，用以定義一組相關的具名常數。  當列舉的具名常數可以有意義地加以結合時，會將 FlagsAttribute 套用至此列舉。|  
|[CA1028：列舉儲存區應該是 Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)|列舉型別是一種實值型別 \(Value Type\)，用以定義一組相關的具名常數。  根據預設，System.Int32 資料型別會用於儲存常數值。  雖然您可以變更這個基礎型別，但是大多數案例中仍不需要或不建議進行變更。|  
|[CA1030：建議在適當時使用事件](../Topic/CA1030:%20Use%20events%20where%20appropriate.md)|此規則會偵測具有事件常用名稱的方法。  如果方法因回應清楚定義的狀態變更而被呼叫，應該由事件處理常式叫用該方法。  呼叫方法的物件應該要引發事件，而不是直接呼叫方法。|  
|[CA1031：不要攔截一般例外狀況類型](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)|不應該攔截一般例外狀況。  請攔截較明確的例外狀況，或重新擲回一般例外狀況當做 catch 區塊中的最後一個陳述式。|  
|[CA1032：必須實作標準例外狀況建構函式](../code-quality/ca1032-implement-standard-exception-constructors.md)|無法提供整組的建構函式會導致難以正確地處理例外狀況。|  
|[CA1033：介面方法應該要可以由子類型呼叫](../Topic/CA1033:%20Interface%20methods%20should%20be%20callable%20by%20child%20types.md)|非密封外部可見的型別會提供公用介面的明確方法實作，但未提供同名的替代外部可見方法。|  
|[CA1034：巢狀類型不應為可見](../code-quality/ca1034-nested-types-should-not-be-visible.md)|巢狀型別是在其他型別範圍內宣告的型別。  巢狀型別可用來封裝包含型別 \(Containing Type\) 私用的 \(Private\) 實作細節。  因為有這樣的用途，所以巢狀型別不應為外部可見的。|  
|[CA1035：ICollection 實作包含強類型成員](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|這項規則要求 ICollection 實作提供強型別成員，讓使用者在使用介面所提供的功能時，不需將引數轉換為 Object 型別。  這項規則假設實作 ICollection 的型別會這樣做，以管理效力比 Object 還強之型別的執行個體集合。|  
|[CA1036：必須在 Comparable 類型中覆寫方法](../code-quality/ca1036-override-methods-on-comparable-types.md)|公用或受保護的型別實作 System.IComparable 介面。  它不會覆寫 Object.Equals，也不會多載等號、不等、小於或大於的語言特定比較運算子。|  
|[CA1038：列舉程式應該是強類型](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|此規則要求 IEnumerator 實作同時也提供 Current 屬性的強型別版本，如此當使用者使用介面提供的功能時，就不需要將傳回值轉型為強型別。|  
|[CA1039：清單為強類型](../code-quality/ca1039-lists-are-strongly-typed.md)|這項規則要求 IList 實作提供強型別成員，讓使用者在使用介面所提供的功能時，不需將引數轉換為 System.Object 型別。|  
|[CA1040：避免空的介面](../Topic/CA1040:%20Avoid%20empty%20interfaces.md)|介面是用來定義一組可提供行為或程式使用合約的成員。  不論型別出現在繼承階層架構 \(Inheritance Hierarchy\) 中的何處，任何型別都可以採用介面所描述的功能。  型別會實作介面，方法是提供介面成員的實作。  空白介面不會定義任何成員，因此也不會定義能夠實作的合約。|  
|[CA1041：提供 ObsoleteAttribute 訊息](../Topic/CA1041:%20Provide%20ObsoleteAttribute%20message.md)|型別或成員是使用並未指定其 ObsoleteAttribute.Message 屬性 \(Property\) 的 System.ObsoleteAttribute 屬性 \(Attribute\) 來標記。  編譯使用 ObsoleteAttribute 來標記的型別或成員之後，會顯示屬性 \(Attribute\) 的 Message 屬性 \(Property\)，以便提供使用者有關過時型別或成員的資訊。|  
|[CA1043：必須針對索引子使用整數類或字串引數](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|索引子 \(也就是索引的屬性\) 應該使用整數型別或字串型別的索引。  這些型別通常會用於資料結構的索引，可以提升程式庫的可用性。  Object 型別的使用應限制於無法在設計階段指定特定整數型別或字串型別的情況。|  
|[CA1044：屬性不應為唯寫](../code-quality/ca1044-properties-should-not-be-write-only.md)|雖然它是可接受並經常需要具有唯讀屬性，設計方針會禁止使用唯寫屬性的屬性。  這是因為讓使用者，設定一個值，然後防止使用者檢視值並不會提供任何安全性。  同時，如果沒有讀取權限，則無法檢視共用物件的狀態，進而限制這些物件的使用性。|  
|[CA1045：不要以傳址方式傳遞類型](../code-quality/ca1045-do-not-pass-types-by-reference.md)|以傳址方式傳遞型別時 \(使用 out 或 ref\)，您需要擁有使用指標的經驗、了解實值型別和參考型別之間的差異，並處理具有多個傳回值的方法。  目標為一般使用者的程式庫架構設計人員不應預期使用者會熟練地運用 out 或 ref 參數。|  
|[CA1046：請勿多載參考類型上的等號比較運算子](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|對參考型別而言，等號比較運算子的預設實作 \(Implementation\) 永遠都是正確的。  根據預設，只有當兩項參考都指向相同物件時才會相等。|  
|[CA1047：不要在密封類型中宣告 protected 成員](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|型別會宣告 protected 成員，如此繼承的型別即可存取或覆寫成員。  根據定義，密封型別無法被繼承，這表示無法呼叫密封型別上的受保護方法。|  
|[CA1048：不要在密封類型中宣告 virtual 成員](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|型別會將方法宣告為 virtual，讓繼承型別可以覆寫 virtual 方法的實作。  根據預設，密封型別無法被繼承。  這會讓密封型別上的虛擬方法失去意義。|  
|[CA1049：擁有原生資源的類型應為可處置](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|配置 Unmanaged 資源的型別應實作 IDisposable，讓呼叫端視需要釋放這些資源，並且縮短持有資源之物件的存留期。|  
|[CA1050：在命名空間中宣告類型](../code-quality/ca1050-declare-types-in-namespaces.md)|型別會在命名空間之內宣告以防止名稱衝突，而且可當做組織物件階層架構中相關型別的一種方法。|  
|[CA1051：不要宣告可見的執行個體欄位](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|欄位的主要用法應該是當做實作詳細資料。  欄位應該是私用或內部的，而且應使用屬性公開。|  
|[CA1052：靜態預留位置類型應該為密封的](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|公用或受保護的型別只包含靜態成員，因此不會利用 sealed \(C\#\) 或 NotInheritable \(Visual Basic\) 修飾詞宣告它們。  預定不會繼承的型別應該使用 sealed 修飾詞來標記，以禁止使用它做為基底型別。|  
|[CA1053：靜態預留位置類型不應包含建構函式](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|公用或巢狀公用型別只宣告靜態成員，而且具有公用或保護的預設建構函式。  建構函式不是必要的，因為呼叫靜態成員不需型別的執行個體。  為了安全，字串多載應該使用字串引數來呼叫統一資源識別項 \(URI\) 多載。|  
|[CA1054：URI 參數不應該為字串](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|如果方法使用 URI 字串表示，應該提供採用 URI 類別的對應多載，這樣就可以透過安全的方式提供這些服務。|  
|[CA1055：URI 傳回值不應該為字串](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|這項規則假設方法會傳回 URI。  URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。  System.Uri 類別以安全的方式提供這些服務。|  
|[CA1056：URI 屬性不應該為字串](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|這項規則假設屬性代表 URI。  URI 的字串表示方式容易發生剖析和編碼錯誤，並且可能因此產生安全性弱點。  System.Uri 類別以安全的方式提供這些服務。|  
|[CA1057：字串 URI 多載呼叫 System.Uri 多載](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|型別會宣告方法多載，這些方法多載的差別只在於以 System.Uri 參數取代字串參數。  接受字串參數的多載不會呼叫接受 URI 參數的多載。|  
|[CA1058：類型不應該擴充特定的基底類型](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|外部可見的型別會延伸某些基底型別 \(Base Type\)。  請使用其他作法。|  
|[CA1059：成員不應該公開特定的具象類型](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|具象型別就是具有完整實作 \(Implementation\) 且因此能加以具現化 \(Instantiated\) 的型別。  若要讓成員能廣泛使用，請使用建議的介面來取代具象型別。|  
|[CA1060：將 P\/Invokes 移到 NativeMethods 類別](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|平台引動方法 \(例如以 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> 標記的方法，或在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中使用 Declare 關鍵字定義的方法\) 都會存取 Unmanaged 程式碼。  這些方法應該是 NativeMethods、SafeNativeMethods 或 UnsafeNativeMethods 類別。|  
|[CA1061：不要隱藏基底類別方法](../code-quality/ca1061-do-not-hide-base-class-methods.md)|只有在衍生方法的參數簽章因型別衍生時比基底方法參數簽章中的型別還要弱時，基底型別中的方法才會被衍生型別中的相同具名方法所隱藏。|  
|[CA1062：驗證公用方法的引數](../code-quality/ca1062-validate-arguments-of-public-methods.md)|所有傳遞至外部可見方法的參考引數都應經過 null 檢查。|  
|[CA1063：必須正確實作 IDisposable](../code-quality/ca1063-implement-idisposable-correctly.md)|所有的 IDisposable 型別都需正確地實作 Dispose 模式。|  
|[CA1064：例外狀況必須是公用](../Topic/CA1064:%20Exceptions%20should%20be%20public.md)|內部例外狀況只會在自己的內部範圍內顯示。  當例外狀況超出內部範圍後，只能使用基本例外狀況來攔截例外狀況。  如果內部例外狀況是繼承自 <xref:System.Exception?displayProperty=fullName>、<xref:System.SystemException?displayProperty=fullName> 或 <xref:System.ApplicationException?displayProperty=fullName>，外部程式碼就沒有足夠的資訊可以知道應該如何處理此例外狀況。|  
|[CA1065：不要在非預期的位置中引發例外狀況](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|不可擲回例外狀況 \(Exception\) 的方法卻擲回例外狀況。|  
|[CA2210：組件應包含有效的強式名稱](../Topic/CA2210:%20Assemblies%20should%20have%20valid%20strong%20names.md)|強式名稱可避免用戶端在不知情的狀況下，載入已遭他人修改的組件。  除了極少數的案例以外，您都應該避免部署沒有強式名稱的組件。  如果您共用或散發未正確簽署的組件，表示這個組件或許已遭他人修改，Common Language Runtime 可能不會載入組件，或是使用者可能必須停用電腦上的驗證作業。|