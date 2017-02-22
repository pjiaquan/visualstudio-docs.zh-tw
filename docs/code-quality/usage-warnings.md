---
title: "用法警告 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.usagerules"
helpviewer_keywords: 
  - "警告，用法"
  - "Managed 程式碼分析警告，用法警告"
  - "用法警告"
ms.assetid: fe7dc2a3-289d-4bf7-a1e4-0947a81287c4
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 用法警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

用法警告會支援 .NET Framework 的正確用法。  
  
## 在本節中  
  
|規則|說明|  
|--------|--------|  
|[CA1801：必須檢視未使用的參數](../Topic/CA1801:%20Review%20unused%20parameters.md)|方法簽章包括不用於方法主體中的參數；|  
|[CA1806：不要忽略方法的結果](../code-quality/ca1806-do-not-ignore-method-results.md)|已建立但從未使用新物件、已呼叫會建立並傳回新字串的方法，而新字串從未使用過，或者 COM 或 P\/Invoke 方法傳回從未使用的 HRESULT 或錯誤碼。|  
|[CA1816：正確呼叫 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|屬於 Dispose 實作的方法不會呼叫 GC.SuppressFinalize，或不屬於 Dispose 實作的方法會呼叫 GC.SuppressFinalize，或呼叫 GC.SuppressFinalize 並傳遞非 this \(在 Visual Basic 中為 Me\) 的方法。|  
|[CA2200：請重新擲回以保存堆疊詳細資料](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|例外狀況遭到重新擲回，而且已在 throw 陳述式中明確指定此例外狀況。  如果例外狀況是透過在陳述式中指定例外狀況而重新擲回，則會遺失在擲回例外狀況之原始方法和目前方法之間呼叫的方法清單。|  
|[CA2201：不要引發保留的例外狀況類型](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|這將使原始錯誤變得難以偵測及偵錯。|  
|[CA2202：不要多次處置物件](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|方法實作包含程式碼路徑，可在相同物件上造成多個 System.IDisposable.Dispose 呼叫或 Dispose 對等用法 \(例如，部分型別上的 Close\(\) 方法\)。|  
|[CA2204：常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|方法主體中的常值 \(Literal\) 字串包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。|  
|[CA2205：必須使用 Win32 API 的 Managed 對應項](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|已定義平台叫用方法，而且 .NET Framework Class Library 中有具同等功能的方法存在。|  
|[CA2207：必須初始化實值類型的靜態欄位內嵌](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|實值型別會宣告明確的靜態建構函式。  若要修正此規則的違規情形，請在宣告所有靜態資料時將靜態資料初始化，並移除靜態建構函式。|  
|[CA2208：請正確執行個體化引數例外狀況](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|對例外狀況型別為 \(或衍生自\) ArgumentException 的預設 \(無參數\) 建構函式進行呼叫，或將錯誤的字串引數傳遞至例外狀況型別為 \(或衍生自\) ArgumentException 的參數化建構函式。|  
|[CA2211：非常數欄位不應該為可見的](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|既非常數，亦非唯讀的靜態欄位不是安全執行緒。  必須小心控制對這類欄位的存取，而且需要進階的程式設計技巧同步 \(Synchronize\) 對類別物件的存取。|  
|[CA2212：不要以 WebMethod 標記 Serviced 元件](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|型別中繼承自 System.EnterpriseServices.ServicedComponent 的方法是以  System.Web.Services.WebMethodAttribute 標示。  因為 WebMethodAttribute 和 ServicedComponent 方法具有衝突的內容和交易流程的行為及需求，所以方法的行為在某些情節中會是不正確的。|  
|[CA2213：可處置的欄位應該受到處置](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|實作 System.IDisposable 的型別宣告了也實作 IDisposable 之型別的欄位。  宣告型別的 Dispose 方法不會呼叫欄位的 Dispose 方法。|  
|[CA2214：不要呼叫建構函式中的可覆寫方法](../Topic/CA2214:%20Do%20not%20call%20overridable%20methods%20in%20constructors.md)|當建構函式呼叫虛擬方法時，有可能尚未執行叫用此方法之執行個體的建構函式。|  
|[CA2215：Dispose 方法應該呼叫基底類別處置](../code-quality/ca2215-dispose-methods-should-call-base-class-dispose.md)|如果型別會繼承自可處置的型別，則必須從本身的 Dispose 方法呼叫基底型別的 Dispose 方法。|  
|[CA2216：可處置類型應該宣告完成項](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|實作 System.IDisposable 且具有建議 Unmanaged 資源用法之欄位的型別，未實作如 Object.Finalize 所述的完成項。|  
|[CA2217：不要以 FlagsAttribute 標記列舉](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|從外部可見的列舉會以 FlagsAttribute 標記，並且有一個或多個不是二的次方，或組合列舉上其他定義值之次方的值。|  
|[CA2218：覆寫 Equals 時必須一併覆寫 GetHashCode](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)|GetHashCode 會依據目前執行個體傳回值，適用於雜湊演算法和資料結構，如雜湊資料表。  兩個型別相同且相等的物件必須傳回相同的雜湊程式碼。|  
|[CA2219：不要在 exception 子句中引發例外狀況](../Topic/CA2219:%20Do%20not%20raise%20exceptions%20in%20exception%20clauses.md)|在 finally 或 fault 子句中引發例外狀況時，新的例外狀況會隱藏作用中的例外狀況。  在 filter 子句中引發例外狀況時，執行階段會以無訊息模式攔截例外狀況。  這將使原始錯誤變得難以偵測及偵錯。|  
|[CA2220：完成項應該呼叫基底類別完成項](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|最終化必須透過繼承階層架構 \(Inheritance Hierarchy\) 進行傳播。  若要確保這一點，則型別必須在它們自己的 Finalize 方法中呼叫基底類別 Finalize 方法。|  
|[CA2221：完成項應該受到保護](../code-quality/ca2221-finalizers-should-be-protected.md)|完成項必須使用系列存取修飾詞 \(Modifier\)。|  
|[CA2222：請勿降低繼承成員的可視性](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|您不得變更繼承成員的存取修飾詞 \(Modifier\)。  將繼承成員變更為私用不會防止呼叫端存取方法的基底類別 \(Base Class\) 實作。|  
|[CA2223：成員不應該只有在傳回類型上不同](../Topic/CA2223:%20Members%20should%20differ%20by%20more%20than%20return%20type.md)|雖然 Common Language Runtime 允許使用傳回型別區分其他部分都相同的成員，但這個功能不屬於 Common Language Specification，也不是 .NET 程式語言共通的功能。|  
|[CA2224：多載等號比較運算子時必須一併覆寫 Equals](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|public 型別會實作等號比較運算子，但不會覆寫 Object.Equals。|  
|[CA2225：運算子多載必須有具名的替代方法](../Topic/CA2225:%20Operator%20overloads%20have%20named%20alternates.md)|偵測到運算子多載，且找不到預期的具名替代方法。  具名的替代成員會提供與運算子相同的功能存取，並且可供以不支援多載運算子 \(Overloaded Operator\) 的語言設計程式的開發人員使用。|  
|[CA2226：運算子應該有對稱的多載](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|型別實作等號比較運算子或不等比較運算子，但未實作相反的運算子。|  
|[CA2227：集合屬性應該為唯讀](../code-quality/ca2227-collection-properties-should-be-read-only.md)|可寫入的集合屬性允許使用者以不同的集合來取代該集合。  唯讀屬性會從取代過程中停止集合，但是仍然允許設定個別成員。|  
|[CA2228：不要使用尚未發行版本所支援的格式建置資源](../Topic/CA2228:%20Do%20not%20ship%20unreleased%20resource%20formats.md)|使用 .NET Framework 發行前版本建置的資源檔，可能無法讓 .NET Framework 的支援版本使用。|  
|[CA2229：請實作序列化建構函式](../code-quality/ca2229-implement-serialization-constructors.md)|若要修正此規則的違規情形，請實作序列化建構函式。  針對密封類別，讓建構函式成為 private，否則為 protected。|  
|[CA2230：必須使用 params 做為變數引數](../code-quality/ca2230-use-params-for-variable-arguments.md)|公用或保護的型別包含使用 VarArgs 呼叫慣例之公用或保護的方法，而不是 params 關鍵字。|  
|[CA2231：覆寫 ValueType.Equals 時必須一併多載等號比較運算子](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|實值型別會覆寫 Object.Equals，但不會實作等號比較運算子。|  
|[CA2232：以 STAThread 標記 Windows Form 進入點](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|STAThreadAttribute 表示應用程式的 COM 執行緒模型為單一執行緒 Apartment。  在使用 Windows Form 的任何應用程式之進入點上必須有此屬性。如果省略的話，Windows 元件就無法正常運作。|  
|[CA2233：運算不應該發生溢位](../code-quality/ca2233-operations-should-not-overflow.md)|如果沒有先驗證運算元，以確定運算結果不會超過所包含之資料型別的可能值範圍，則不應執行算術運算。|  
|[CA2234：必須傳遞 System.Uri 物件，而不要傳遞字串](../Topic/CA2234:%20Pass%20System.Uri%20objects%20instead%20of%20strings.md)|呼叫字串參數名稱包含 "uri"、"URI"、"urn"、"URN"、"url" 或 "URL"，而且此方法的宣告型別會包含具有 System.Uri 參數的對應方法多載。|  
|[CA2235：必須標記所有不可序列化的欄位](../code-quality/ca2235-mark-all-non-serializable-fields.md)|可序列化之型別中所宣告之型別的執行個體 \(Instance\) 欄位是不可序列化的。|  
|[CA2236：必須呼叫 ISerializable 類型上的基底類別方法](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|若要修正此規則的違規情形，請從對應的衍生型別方法或建構函式，呼叫基底型別 GetObjectData 方法或序列化建構函式。|  
|[CA2237：必須以 SerializableAttribute 標記 ISerializable 類型](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|若要讓 Common Language Runtime 辨認為可序列化，即使型別透過 ISerializable 介面的實作使用自訂序列化常式，型別仍必須以 SerializableAttribute 屬性標記。|  
|[CA2238：請正確實作序列化方法](../code-quality/ca2238-implement-serialization-methods-correctly.md)|處理序列化事件的方法沒有正確的簽章、傳回型別或可視性。|  
|[CA2239：必須為選擇性欄位提供還原序列化方法](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|型別具有以 System.Runtime.Serialization.OptionalFieldAttribute 屬性標示的欄位，而且型別不提供還原序列化事件處理方法。|  
|[CA2240：必須正確實作 ISerializable](../Topic/CA2240:%20Implement%20ISerializable%20correctly.md)|若要修正此規則的違規情形，請將 GetObjectData 方法設為可見和可覆寫的，並確定所有執行個體欄位都加入序列化處理序中，或已明確標記 NonSerializedAttribute 屬性。|  
|[CA2241：必須提供格式化方法的正確引數](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|傳遞至 System.String.Format 的格式引數不包含對應至每個物件引數的格式項目，反之亦然。|  
|[CA2242：必須正確測試 NaN](../code-quality/ca2242-test-for-nan-correctly.md)|此運算式針對 Single.Nan 或 Double.Nan 測試值。  使用 Single.IsNan\(Single\) 或 Double.IsNan\(Double\) 即可測試值。|  
|[CA2243：屬性字串常值必須正確剖析](../code-quality/ca2243-attribute-string-literals-should-parse-correctly.md)|屬性的字串常值參數未針對 URL、GUID 或版本進行正確剖析。|