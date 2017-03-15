---
title: "CA2233：運算不應該發生溢位 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperationsShouldNotOverflow"
  - "CA2233"
helpviewer_keywords: 
  - "CA2233"
  - "OperationsShouldNotOverflow"
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2233：運算不應該發生溢位
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|型別名稱|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|分類|Microsoft.Usage|  
|中斷變更|不中斷|  
  
## 原因  
 方法會執行算術運算，但不會預先驗證運算元以防止溢位。  
  
## 規則描述  
 如果沒有先驗證運算元，以確定運算結果不會超過所包含之資料型別的可能值範圍，則不應執行算術運算。  根據執行內容和所包含的資料型別，數學溢位可能會導致 <xref:System.OverflowException?displayProperty=fullName> 或結果的最重要位元遭到捨棄。  
  
## 如何修正違規  
 若要修正此規則的違規情形，請在執行作業之前先驗證運算元。  
  
## 隱藏警告的時機  
 如果運算元的可能值從未導致算術運算溢位，則您可以放心地隱藏對這項規則的警告。  
  
## 違規範例  
  
### 描述  
 下列範例中的方法會管理違反此規則的整數。  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 需要停用**移除**整數溢位選項才能引發此項。  
  
### 程式碼  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-cs[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### 註解  
 如果這個範例中的方法是傳遞 <xref:System.Int32.MinValue?displayProperty=fullName>，運算就會反向溢位 \(Underflow\)。  這會造成結果的最高有效位元被捨棄。  下列程式碼顯示發生這個現象的方式。  
  
 \[C\#\]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 \[VB\]  
  
```  
Public Shared Sub Main()       
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648   
    value = Calculator.Decrement(value)   
    Console.WriteLine(value)   
End Sub  
```  
  
### Output  
  
```  
2147483647  
```  
  
## 使用輸入參數驗證進行修正  
  
### 描述  
 下列範例會藉由驗證輸入值來修正前述違規。  
  
### 程式碼  
 [!CODE [FxCop.Usage.OperationOverflowFixed#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed#1)]  
  
## 使用檢查區塊進行修正  
  
### 描述  
 下列範例會藉由在檢查區塊中包裝運算來修正前述違規。  如果運算造成溢位，將會擲回 <xref:System.OverflowException?displayProperty=fullName>。  
  
 請注意，[!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 不支援檢查區塊。  
  
### 程式碼  
 [!CODE [FxCop.Usage.OperationOverflowChecked#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked#1)]  
  
## 開啟檢查算術溢位\/反向溢位  
 如果在 C\# 中開啟檢查算術溢位\/反向溢位，就等同於將每個整數運算包裝在檢查區塊中。  
  
 **若要在 C\# 中開啟檢查算術溢位\/反向溢位**  
  
1.  在 \[**方案總管**\] 中，以滑鼠右鍵按一下專案，並選擇 \[**屬性**\]。  
  
2.  選取 \[**建置**\] 索引標籤，並按一下 \[**進階**\]。  
  
3.  選取 \[**檢查算術溢位\/反向溢位**\]，並按一下 \[**確定**\]。  
  
## 請參閱  
 <xref:System.OverflowException?displayProperty=fullName>   
 [C\# 運算子](/dotnet/csharp/language-reference/operators/index)   
 [Checked 與 Unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)