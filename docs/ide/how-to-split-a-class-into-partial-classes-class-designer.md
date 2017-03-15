---
title: "How to: Split a Class into Partial Classes (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer, partial classes"
  - "partial classes, Class Designer"
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# How to: Split a Class into Partial Classes (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

您可以使用 `Partial` 關鍵字 \(在 Visual Basic 中\) 或 `partial` 關鍵字 \(在 Visual C\# 中\)，將類別 \(Class\) 或結構的宣告分割成數個宣告。  您可以將任意數目的部分宣告存放在任意數目的不同原始程式檔 \(Source File\) 中，或單一原始程式檔中。  不過，所有的宣告都必須位於相同的組件 \(Assembly\) 和命名空間中。  
  
 部分類別適用於數種情況。  例如，處理大型專案時，將類別分割成多個檔案，可以讓多位程式設計人員同時處理專案。  當您使用 Visual Studio 產生的程式碼時，可以變更類別而不需重新建立原始程式檔   \(Visual Studio 產生的程式碼範例包括 Windows Form 和 Web 服務包裝函式程式碼\)。 因此，您可以使用自動產生的類別建立程式碼，而不需修改 Visual Studio 建立的檔案。  
  
 部分方法有兩種。  在 Visual C\# 中，它們分別稱為宣告 \(Declaring\) 和實作 \(Implementing\)，在 Visual Basic 中，則分別稱為宣告 \(Declaration\) 和實作 \(Implementation\)。  
  
 \[類別設計工具\] 支援部分類別和方法。  類別圖表中的型別圖案是指部分類型的單一宣告位置。  如果部分類別是在多個檔案中定義，您可以設定 \[**屬性**\] 視窗中的 \[**New Member Location**\] 屬性，藉此指定類別設計工具將使用的宣告位置。  也就是說，當您按兩下類別圖案，類別設計工具會移至包含由 \[**New Member Location**\] 屬性識別之類別宣告的原始程式檔。  當您按兩下類別圖案中的部分方法，類別設計工具就會移至部分方法宣告。  此外，\[**屬性**\] 視窗中的 \[**File Name**\] 屬性同樣會參考宣告位置。  部分類別的 \[**File Name**\] 會同時列出包含該類別之宣告和實作程式碼的所有檔案。  不過，部分方法的 \[**File Name**\] 則只會列出包含部分方法宣告的檔案。  
  
 下列範例會將 `Employee` 類別的定義分割成兩個宣告，其中每個宣告都定義不同的程序。  範例中的這兩個部分定義可以位於單一原始程式檔中，也可以位於兩個不同的原始程式檔中。  
  
> [!NOTE]
>  Visual Basic 使用部分類別定義將 Visual Studio 產生的程式碼與使用者撰寫的程式碼分開。  程式碼會分散在不同的原始程式碼檔案中。  例如，\[**Windows Form 設計工具**\] 會定義控制項的部分類別 \(例如 `Form`\)。  您不應該修改這些控制項中所產生的程式碼。  
  
 如需 Visual Basic 中之部分型別的詳細資訊，請參閱 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)。  
  
## 範例  
 若要在 Visual Basic 中分割類別定義，請使用 `Partial` 關鍵字，如下列範例所示。  
  
```vb#  
' First part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateWorkHours()  
    End Sub  
End Class  
  
' Second part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateTaxes()  
    End Sub  
End Class  
```  
  
## 範例  
 若要在 Visual C\# 中分割類別定義，請使用 `partial` 關鍵字 \(如下列範例所示\)。  
  
```c#  
// First part of class definition.  
public partial class Employee  
{  
    public void CalculateWorkHours()  
    {  
    }  
}  
  
// Second part of class definition.  
public partial class Employee  
{  
    public void CalculateTaxes()  
    {  
    }  
}  
```  
  
## 請參閱  
 [部分類別和方法](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [partial \(類型\)](/dotnet/csharp/language-reference/keywords/partial-type)   
 [partial \(方法\) \(C\# 參考\)](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)