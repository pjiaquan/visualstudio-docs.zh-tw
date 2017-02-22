---
title: "CA1024：建議在適當時使用屬性 | Microsoft Docs"
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
  - "UsePropertiesWhereAppropriate"
  - "CA1024"
helpviewer_keywords: 
  - "CA1024"
  - "UsePropertiesWhereAppropriate"
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1024：建議在適當時使用屬性
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|UsePropertiesWhereAppropriate|  
|CheckId|CA1024|  
|分類|Microsoft.Design|  
|中斷變更|中斷|  
  
## 原因  
 公用或保護的方法具有以 `Get` 開始的名稱，該名稱不採用任何參數並且會傳回不是陣列的值。  
  
## 規則描述  
 在大部分情況下，屬性代表資料，而方法會執行動作。  存取屬性就如同存取欄位，這會讓使用屬性更為容易。  如果下列其中一個條件存在，則方法是成為屬性的不錯候選者：  
  
-   不採用任何引數，而且會傳回物件的狀態資訊。  
  
-   接受單一引數，以設定物件狀態的某部分。  
  
 屬性應該以如同欄位般的方式運作。若方法不是這種運作方式，則不應該變更為屬性。  在下列狀況中，使用方法比使用屬性更為適合：  
  
-   方法用來執行較耗時的作業。  這個方法感覺上會比設定或取得欄位值所需的時間更耗時。  
  
-   方法用來執行轉換作業。  存取欄位並不會傳回它所儲存之資料轉換後的版本。  
  
-   Get 方法有個明顯的副作用。  擷取欄位的值並不會產生任何副作用。  
  
-   執行的順序是很重要的。  設定欄位值不會依賴其他作業的發生。  
  
-   連續呼叫方法兩次會建立不同的結果。  
  
-   方法是靜態 \(Static\)，但卻會傳回呼叫端可變更的物件。  擷取欄位值不允許呼叫端變更欄位所儲存的資料。  
  
-   方法會傳回陣列。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請將方法變更為屬性。  
  
## 隱藏警告的時機  
 如果方法至少會符合先前所列的其中一項準則，請隱藏這項規則的警告。  
  
## 在偵錯工具中控制屬性展開  
 程式設計人員會避免使用屬性的一個原因是不希望偵錯工具自動展開屬性。  例如，屬性可能牽涉到配置大型物件或呼叫 P\/Invoke，但實際上卻不見得有任何明顯的副作用。  
  
 藉由套用 <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>，即可以防止偵錯工具自動展開屬性。  下列範例顯示如何將這個屬性 \(Attribute\) 套用到執行個體屬性 \(Property\)。  
  
```vb  
Imports System   
Imports System.Diagnostics   
  
Namespace Microsoft.Samples   
  
    Public Class TestClass   
  
        ' [...]   
  
        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _   
        Public ReadOnly Property LargeObject() As LargeObject   
            Get   
                ' Allocate large object   
                ' [...]   
            End Get   
        End Property   
  
    End Class   
  
End Namespace  
```  
  
```c#  
  
        using System;   
using System.Diagnostics;   
  
namespace Microsoft.Samples   
{   
    public class TestClass   
    {   
        // [...]   
  
        [DebuggerBrowsable(DebuggerBrowsableState.Never)]   
        public LargeObject LargeObject   
        {   
            get   
            {   
                // Allocate large object   
                // [...]   
  
        }  
    }  
}  
```  
  
## 範例  
 下列範例包含數個應轉換為屬性的方法，以及數個因行為不像欄位而不應該轉換的方法。  
  
 [!code-cs[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]