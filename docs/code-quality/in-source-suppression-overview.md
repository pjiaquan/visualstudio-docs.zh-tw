---
title: "原始檔中隱藏項目概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "來源隱藏，程式碼分析"
  - "程式碼分析，來源隱藏"
ms.assetid: f1a2dc6a-a9eb-408c-9078-2571e57d207d
caps.latest.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 40
---
# 原始檔中隱藏項目概觀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

原始檔中隱藏項目的功能可透過將 **SuppressMessage** 屬性加入至導致違規的程式碼區段，隱藏或忽略 Managed 程式碼中的程式碼分析違規。  **SuppressMessage** 屬性是條件屬性；只有當您在編譯時期定義了 CODE\_ANALYSIS 條件式編譯符號時，這個屬性才會包含在 Managed 程式碼的 IL 中繼資料中。  
  
 在 C\+\+\/CLI 中，若要加入此屬性，請在標頭檔中使用 CA\_SUPPRESS\_MESSAGE 或 CA\_GLOBAL\_SUPPRESS\_MESSAGE 巨集。  
  
 您不應在發行的組建上使用原始檔中隱藏項目的功能，以免不慎發行了原始檔中隱藏項目的中繼資料。  處理原始檔中隱藏項目所耗用的資源不低，因此若納入原始檔中隱藏項目的中繼資料，可能會降低應用程式的效能。  
  
> [!NOTE]
>  您不需要自己親手撰寫這些屬性。  如需詳細資訊，請參閱[如何：使用功能表項目隱藏警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)。  此功能表項目不適用於 C\+\+ 程式碼。  
  
## SuppressMessage 屬性  
 當您以滑鼠右鍵按一下 \[**錯誤清單**\] 中的程式碼分析警告，然後按一下 \[**隱藏訊息**\] 時，您的程式碼或是專案的全域隱藏項目檔案中便會加入 **SuppressMessage** 屬性。  
  
 **SuppressMessage** 屬性具有下列格式：  
  
```vb  
<Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")>  
```  
  
```c#  
[Scope:SuppressMessage("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")]  
  
```  
  
 \[C\+\+\]  
  
```  
CA_SUPPRESS_MESSAGE("Rule Category", "Rule Id", Justification = "Justification", MessageId = "MessageId", Scope = "Scope", Target = "Target")  
  
```  
  
 其中：  
  
-   **Rule Category**：在其中定義規則的分類。  如需程式碼分析規則分類的詳細資訊，請參閱 [Managed 程式碼的程式碼分析警告](../code-quality/code-analysis-for-managed-code-warnings.md)。  
  
-   **Rule Id**：規則的識別項。  支援規則識別項的簡短名稱和完整名稱。  簡短名稱為 CAXXXX，而完整名稱為 CAXXXX:FriendlyTypeName。  
  
-   **Justification**：記錄隱藏訊息原因的文字。  
  
-   **Message Id**：每個訊息之問題的唯一識別項。  
  
-   **Scope**：要隱藏警告的目標。  如果未指定目標，就會將目標設定為屬性的目標。  支援的範圍包括下列：  
  
    -   Module  
  
    -   命名空間  
  
    -   資源  
  
    -   類型  
  
    -   成員  
  
-   **Target**：用來在要隱藏的警告上指定目標的識別項。  此識別項必須包含完整的項目名稱。  
  
## SuppressMessage 用法  
 程式碼分析警告會隱藏在套用 **SuppressMessage** 屬性執行個體 \(Instance\) 的層級。  目的是為了讓隱藏資訊與發生違規的程式碼緊密結合。  
  
 隱藏項目的一般格式包括了規則分類和規則識別項，其中規則識別項包含人們可讀取的 \(Human\-Readable\) 選用規則名稱表示。  例如：  
  
 `[SuppressMessage("Microsoft.Design", "CA1039:ListsAreStrongTyped")]`  
  
 若有絕對的效能原因，而必須將原始檔中隱藏項目的中繼資料最小化，則可以省略規則名稱本身。  將規則分類和它的規則 ID 結合，即足以構成唯一的規則識別項。  例如：  
  
 `[SuppressMessage("Microsoft.Design", "CA1039")]`  
  
 基於維護工作的考量，並不建議使用這個格式。  
  
## 在方法主體內隱藏多個違規  
 屬性只能套用至方法，不可內嵌於方法主體中。  不過，您可以指定識別項做為訊息 ID，以區別在方法內發生的多次違規。  
  
 [!code-cpp[InSourceSuppression#1](../code-quality/codesnippet/CPP/in-source-suppression-overview_1.cpp)]
 [!code-vb[InSourceSuppression#1](../code-quality/codesnippet/VisualBasic/in-source-suppression-overview_1.vb)]
 [!code-cs[InSourceSuppression#1](../code-quality/codesnippet/CSharp/in-source-suppression-overview_1.cs)]  
  
## 產生的程式碼  
 Managed 程式碼編譯器 \(Compiler\) 和某些協力廠商工具都會產生程式碼，以協助快速開發程式碼。  編譯器產生的程式碼出現在原始程式檔 \(Source File\) 時，通常都會以 **GeneratedCodeAttribute** 屬性來標記。  
  
 您可以選擇是否隱藏所產生之程式碼的程式碼分析警告和錯誤。  如需如何隱藏這種警告和錯誤的詳細資訊，請參閱 [如何：隱藏所產生程式碼的警告](../code-quality/how-to-suppress-code-analysis-warnings-for-generated-code.md)。  
  
 請注意，程式碼分析會忽略套用到整個組件 \(Assembly\) 或單一參數的 **GeneratedCodeAttribute**，  不過這種情況並不常發生。  
  
## 全域層級的隱藏項目  
 Managed 程式碼分析工具會檢查套用至組件、模組、型別、成員或參數層級的 **SuppressMessage** 屬性，  也會引發資源和命名空間的違規。  這些違規必須套用在全域層級，而且加以指定範圍和目標。  例如，下列訊息會隱藏命名空間違規：  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1020:AvoidNamespacesWithFewTypes", Scope = "namespace", Target = "MyNamespace")]`  
  
> [!NOTE]
>  以命名空間範圍隱藏警告時，只會對命名空間本身隱藏警告，  不會對命名空間內的型別隱藏警告。  
  
 任何隱藏項目都可以藉由指定明確的範圍來表示。  這些隱藏項目必須處於模組層級。  您不能藉由裝飾型別來指定成員層級的隱藏項目。  
  
 如果訊息參照到編譯器所產生的程式碼，但該程式碼並未對應到明確提供的使用者來源，則您只能使用全域層級的隱藏項目來隱藏這些訊息。  例如，下列程式碼會隱藏編譯器發出之建構函式 \(Constructor\) 的違規：  
  
 `[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="Microsoft.Tools.FxCop.Type..ctor()")]`  
  
> [!NOTE]
>  目標一律包含完整的項目名稱。  
  
## 全域隱藏項目檔案  
 全域隱藏項目檔案會維護全域層級隱藏項目或未指定目標的隱藏項目。  例如，組件層次違規的隱藏項目會儲存在這個檔案中。  此外，某些 ASP.NET 隱藏項目也會儲存在這個檔案中，因為表單的後置程式碼無法使用專案層級的設定。  當您第一次在 \[錯誤清單\] 視窗中選取 \[**隱藏訊息**\] 命令的 \[**在專案隱藏項目檔中**\] 選項時，將會建立全域隱藏項目，並加入至您的專案。  如需詳細資訊，請參閱[如何：使用功能表項目隱藏警告](../code-quality/how-to-suppress-warnings-by-using-the-menu-item.md)。  
  
## 請參閱  
 <xref:System.Diagnostics.CodeAnalysis>