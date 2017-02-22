---
title: "CA1704：識別項應該使用正確的拼字 | Microsoft Docs"
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
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
helpviewer_keywords: 
  - "CA1704"
  - "IdentifiersShouldBeSpelledCorrectly"
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1704：識別項應該使用正確的拼字
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|IdentifiersShouldBeSpelledCorrectly|  
|CheckId|CA1704|  
|分類|Microsoft.Naming|  
|中斷變更|中斷|  
  
## 原因  
 識別項的名稱包含一個或多個 Microsoft 拼字檢查程式庫無法辨識的字。  此規則不會檢查建構函式 \(Constructor\) 或特殊名稱成員，例如 get 和 set 屬性存取子。  
  
## 規則描述  
 此規則會將識別項剖析成語彙基元 \(Token\)，並檢查每個語彙基元的拼寫是否正確。  此剖析演算法將會執行下列轉換：  
  
-   大寫字母為新語彙基元的開頭。  例如，MyNameIsJoe 會語彙基元化為 "My"、"Name"、"Is"、"Joe"。  
  
-   如果有多個大寫字母，最後一個大寫字母會開始新的語彙基元。  例如，GUIEditor 會語彙基元化為 "GUI"、"Editor"。  
  
-   移除前後端的所有格符號。  例如，'sender' 會語彙基元化為 "sender"。  
  
-   移除代表語彙基元結尾的底線。  例如，Hello\_world 會語彙基元化為 "Hello"、"world"。  
  
-   移除內嵌連字號 \(&\)。  例如，for&mat 會語彙基元化為 "format"。  
  
 預設會使用英文 \(en\) 版的拼字檢查程式。  目前沒有其他可用的語言字典。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請更正單字的拼寫，或是將單字加入名稱為 CustomDictionary.xml 的自訂字典中。  請將此字典放在工具的安裝目錄、專案目錄或使用者設定檔底下與工具關聯的目錄 \(%USERPROFILE%\\Application Data\\...\) 中。  若要了解如何將自訂字典加入至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中的專案，請參閱 [如何：自訂程式碼分析字典](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)  
  
-   在 Dictionary\/Words\/Recognized 路徑底下加入不會導致違規的單字。  
  
-   在 Dictionary\/Words\/Unrecognized 路徑底下加入應該會導致違規的單字。  
  
-   在 Dictionary\/Words\/Deprecated 路徑底下加入應該標示為已過時的單字。  如需詳細資訊，請參閱相關的規則主題[CA1726：建議使用慣用詞彙](../code-quality/ca1726-use-preferred-terms.md)。  
  
-   將縮略字大小寫規則的例外狀況加入至 Dictionary\/Acronyms\/CasingExceptions 路徑。  
  
 以下顯示自訂字典檔結構的範例。  
  
```  
<Dictionary>  
   <Words>  
      <Unrecognized>  
         <Word>cb</Word>  
      </Unrecognized>  
      <Recognized>  
         <Word>stylesheet</Word>  
         <Word>GotDotNet</Word>  
      </Recognized>  
      <Deprecated>  
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>  
      </Deprecated>  
   </Words>  
   <Acronyms>  
      <CasingExceptions>  
         <Acronym>CJK</Acronym>  
         <Acronym>Pi</Acronym>  
      </CasingExceptions>  
   </Acronyms>  
</Dictionary>  
```  
  
## 隱藏警告的時機  
 只有在故意拼錯單字，而且該單字只適用於一組限定的程式庫時，才能隱藏此規則的警告。  拼寫正確的單字可縮短新軟體程式庫所需的學習過程。  
  
## 相關規則  
 [CA2204：常值必須使用正確的拼字](../code-quality/ca2204-literals-should-be-spelled-correctly.md)  
  
 [CA1703：資源字串應該拼寫正確](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)  
  
 [CA1709：識別項名稱應該使用正確的大小寫](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)  
  
 [CA1708：識別項名稱不應該只靠大小寫區別](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)  
  
 [CA1707：識別項不應包含底線](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)  
  
 [CA1726：建議使用慣用詞彙](../code-quality/ca1726-use-preferred-terms.md)  
  
## 請參閱  
 [如何：自訂程式碼分析字典](../Topic/How%20to:%20Customize%20the%20Code%20Analysis%20Dictionary.md)