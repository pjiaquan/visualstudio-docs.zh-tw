---
title: "效能警告 | Microsoft Docs"
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
  - "vs.codeanalysis.performancerules"
helpviewer_keywords: 
  - "警告，效能"
  - "效能警告"
  - "效能，警告"
  - "Managed 程式碼分析警告，效能警告"
ms.assetid: e014ac3a-02e6-46d9-942c-3491dd63782f
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# 效能警告
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

效能警告會支援高效能的程式庫和應用程式。  
  
## 在本節中  
  
|規則|說明|  
|--------|--------|  
|[CA1800：請勿執行不必要的轉型](../code-quality/ca1800-do-not-cast-unnecessarily.md)|重複轉型會降低效能，尤其是在精簡型態的反覆運算陳述式中執行轉型時。|  
|[CA1801：必須檢視未使用的參數](../Topic/CA1801:%20Review%20unused%20parameters.md)|方法簽章包括不用於方法主體中的參數；|  
|[CA1802：建議在適當時使用常值](../code-quality/ca1802-use-literals-where-appropriate.md)|欄位宣告為 static 和 read\-only \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Shared 和 ReadOnly\)，並使用編譯時期能計算的值進行初始化。  因為指派給目標欄位的值可在編譯時期進行計算，所以將宣告變更為 const \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Const\) 欄位，其值便可於編譯時期進行計算，而不是在執行階段計算。|  
|[CA1804：必須移除未使用的區域變數](../code-quality/ca1804-remove-unused-locals.md)|未使用的區域變數和不必要的設定，會增加組件的大小並降低效能。|  
|[CA1806：不要忽略方法的結果](../code-quality/ca1806-do-not-ignore-method-results.md)|已建立但從未使用新物件、已呼叫會建立並傳回新字串的方法，而新字串從未使用過，或者元件物件模型 \(COM\) 或 P\/Invoke 方法傳回從未使用的 HRESULT 或錯誤碼。|  
|[CA1809：避免使用過多區域變數](../code-quality/ca1809-avoid-excessive-locals.md)|常見的效能最佳化作法是在處理器暫存器中儲存值，而非記憶體，這稱為「註冊 \(Enregistering\) 值」。若要增加所有區域變數都能註冊的機率，請將區域變數的數目限制為 64。|  
|[CA1810：必須初始化參考類型內部的靜態欄位](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|當型別宣告明確的靜態建構函式時，Just\-In\-Time \(JIT\) 編譯器會將檢查加入至型別的每個靜態方法和執行個體建構函式，確保之前已呼叫該靜態建構函式。  靜態建構函式檢查會降低效能。|  
|[CA1811：避免使用未呼叫的私用程式碼](../code-quality/ca1811-avoid-uncalled-private-code.md)|private 或 internal \(組件層級\) 成員在組件中沒有呼叫端，不會由 Common Language Runtime 叫用，而且委派也未叫用該成員。|  
|[CA1812：避免使用未執行個體化的內部類別](../Topic/CA1812:%20Avoid%20uninstantiated%20internal%20classes.md)|組件層級型別的執行個體不是由組件中的程式碼所建立。|  
|[CA1813：避免使用非密封屬性](../code-quality/ca1813-avoid-unsealed-attributes.md)|[!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] Class Library 會提供擷取自訂屬性的方法。  根據預設，這些方法會搜尋屬性繼承階層架構。  密封屬性會減少對整個繼承階層架構的搜尋，並且可以改進效能。|  
|[CA1814：建議使用不規則陣列取代多維陣列](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|不規則陣列是一種陣列，其元素也是陣列。  組成元素的陣列大小可能不相同，因此對於某些資料集而言較不會浪費空間。|  
|[CA1815：覆寫實值類型上的等號和等號比較運算子](../Topic/CA1815:%20Override%20equals%20and%20operator%20equals%20on%20value%20types.md)|對於實值型別而言，Equals 的繼承實作會使用 Reflection 程式庫，並比較所有欄位的內容。  但是 Reflection 相當耗費運算資源，而且可能不需要比較每個欄位是否相等。  如果希望使用者比較或排序執行個體，或是使用執行個體做為雜湊資料表索引鍵，則您的實值型別應實作 Equals。|  
|[CA1816：正確呼叫 GC.SuppressFinalize](../code-quality/ca1816-call-gc-suppressfinalize-correctly.md)|屬於 Dispose 實作的方法不會呼叫 GC.SuppressFinalize，或不屬於 Dispose 實作的方法會呼叫 GC.SuppressFinalize，或呼叫 GC.SuppressFinalize 並傳遞非 this \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Me\) 的方法。|  
|[CA1819：屬性不應傳回陣列](../code-quality/ca1819-properties-should-not-return-arrays.md)|即使屬性是唯讀，所傳回的陣列不會是寫入保護。  若要保持陣列為防止遭他人修改，屬性必須傳回陣列複本。  一般而言，使用者不了解呼叫這類屬性所造成的不良效能影響。|  
|[CA1820：應該使用字串長度測試空白字串](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|使用 String.Length 屬性或 String.IsNullOrEmpty 方法比較字串，明顯地會比使用 Equals 還快。|  
|[CA1821：必須移除空的完成項](../code-quality/ca1821-remove-empty-finalizers.md)|請盡可能避免使用完成項，因為追蹤物件存留期 \(Lifetime\) 時將會產生額外的效能負荷。  空白完成項只會增加額外負荷，而沒有任何好處。|  
|[CA1822：將成員標記為靜態](../Topic/CA1822:%20Mark%20members%20as%20static.md)|不會存取執行個體資料或不會呼叫執行個體方法的成員，可以標記為 static \(在 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 中為 Shared\)。  將方法標記為 static 之後，編譯器將對這些成員發出非虛擬呼叫位置。  這麼做可以讓重視效能的程式碼獲得可觀的效能。|  
|[CA1823：避免包含未使用的私用欄位](../code-quality/ca1823-avoid-unused-private-fields.md)|偵測到似乎不能在組件內存取的私用欄位。|  
|[CA1824：以 NeutralResourcesLanguageAttribute 標記組件](../Topic/CA1824:%20Mark%20assemblies%20with%20NeutralResourcesLanguageAttribute.md)|NeutralResourcesLanguage 屬性 \(Attribute\) 會告知 ResourceManager，用來顯示組件之中性文化特性 \(Culture\) 資源的語言。  這可改善載入第一個資源的查詢效能，而且可以減少您的工作集。|