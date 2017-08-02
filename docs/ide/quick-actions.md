---
title: "快速動作 | Microsoft Docs"
ms.custom: 
ms.date: 05/08/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: e173fb7d-c5bd-4568-ba0f-aa61913b3244
author: kempb
ms.author: kempb
manager: ghogen
dev_langs:
- CSharp
- VB
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 8bf0b097be929b30627e0f1139c6e0b145933ab4
ms.openlocfilehash: ec2ae70312c7cb5f26630246046cadc7c210e1c2
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# 快速動作
<a id="quick-actions" class="xliff"></a>

[快速動作](refactoring-code-generation-quick-actions.md#quick-actions)可讓您輕鬆地重構、產生或用其他方式以單一動作修改程式碼。  雖然有許多專門適用於 C# 或 Visual Basic 的快速動作，也有一些同時適用於 C# 和 Visual Basic 專案。  當您的游標位於適當程式碼行時，這些可以使用燈泡圖示 ![小燈泡圖示](~/docs/ide/media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") 或按 **Ctrl + .** 來套用 。

如果有紅色曲線，而且 Visual Studio 有針對如何修正問題的建議，您就會看到燈泡。 例如，如果紅色曲線指出一個錯誤，當該錯誤有可用的修正時，便會出現燈泡。 針對任何語言，協力廠商都可以提供自訂診斷和建議，例如做為 SDK 的一部分，而 Visual Studio 燈泡會依據這些規則亮燈。  

### 如何看到燈泡
<a id="to-see-a-light-bulb" class="xliff"></a>  

1. 在許多情況下，當您將滑鼠指標停留在錯誤點上方時，會自動出現燈泡；或者當您將插入號移到含有錯誤的字行時，會在編輯器左邊界出現燈泡。 當您看到紅色曲線時，可以將滑鼠暫留在其上方，即可顯示燈泡。 當您使用滑鼠或鍵盤前往發生問題之字行中的任何地方，也可以使燈泡顯示。  

2. 在字行任何地方按 **Ctrl+.**， 可叫用燈泡，直接前往可能的修正方法清單。  

   ![當滑鼠游標暫留時的燈泡](~/docs/ide/media/vs2015_lightbulb_hover.png "VS2017_LightBulb_Hover")  

### 如何看到可能的修正方法
<a id="to-see-potential-fixes" class="xliff"></a>  
按一下向下箭號或 [顯示可能的修正方法] 連結，就會顯示燈泡可以提供給您的快速動作清單。  

![放大的燈泡](../ide/media/vs2015_lightbulb_hover_expanded.png "VS2017_LightBulb_hover_expanded")

## 一般的快速動作
<a id="common-quick-actions" class="xliff"></a>
以下是一些同時適用於 C# 和 Visual Basic 程式碼的一般快速動作。

### 新增遺漏的 Case/預設的 Case/兩者
<a id="add-missing-casesdefault-caseboth" class="xliff"></a>
以 C# 建立 `switch` 陳述式或以 Visual Basic 建立 `Select Case` 陳述式時，您可以使用程式碼動作，自動新增遺漏的 Case 項目、預設的 Case 陳述式，或兩者。  對於如下的空陳述式：

```CSharp
enum MyEnum
{
    Item1,
    Item2,
    Item3
}

...

MyEnum myEnum = MyEnum.Item1;

switch(myEnum)
{
}
```

```VB
Enum MyEnum
    Item1
    Item2
    Item3
End Enum

...

Dim myEnum as MyEnum = MyEnum.Item1

Select Case myEnum
End Select
```

使用 [新增兩者] 快速動作填入遺漏的 Case 和預設 Case 將會建立下列︰

```CSharp
switch(myEnum)
{
    case MyEnum.Item1:
        break;
    case MyEnum.Item2:
        break;
    case MyEnum.Item3:
        break;
    default:
        break;
}
```

```VB
Select Case myEnum
    Case MyEnum.Item1
        Exit Select
    Case MyEnum.Item2
        Exit Select
    Case Else
        Exit Select
End Select
```

### 更正拼字錯誤的類型
<a id="correct-misspelled-type" class="xliff"></a>
如果您不小心拼錯 Visual Studio 中的類型，這個快速動作會自動更正它。  您會看到燈泡功能表中的這些項目**「變更 '*拼字錯誤類型*' 為 '*正確類型*'**。  例如: 

```CSharp
// Before
private viod MyMethod()
{
}

// Change 'viod' to 'void'

// After
private void MyMethod()
{
}
```

```VB
' Before
Function MyFunction as Intger
End Function

' Change 'Intger' to 'Integer'

' After
Function MyFunction as Integer
End Function
```

### 移除不必要的 Cast
<a id="remove-unnecessary-cast" class="xliff"></a>
如果您將類型轉型為不需要轉型的另一種類型，**移除不必要的 Cast** 快速動作項目將會移除您程式碼中的 Cast。

```CSharp
// before
int number = (int)3;

// Remove Unnecessary Cast

// after
int number = 3;
```

```VB
' Before
Dim number as Integer = CType(3, Integer)

' Remove Unnecessary Cast

' After
Dim number as Integer = 3
```

### 以屬性取代方法/以方法取代屬性
<a id="replace-method-with-property--replace-property-with-method" class="xliff"></a>
這些快速動作會將方法轉換為屬性，或反過來轉換。  下列範例顯示從方法變更為屬性。  相反的情況下，只要反轉「之前」和「之後」區段。

```CSharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

```VB
Dim MyValue As Integer

' Before
Function GetMyValue() As Integer
    Return MyValue
End Function

' Replace 'GetMyValue' with property

' After
ReadOnly Property MyValue As Integer
    Get
        Return MyValue
    End Get
End Property
```

### 將方法設為同步
<a id="make-method-synchronous" class="xliff"></a>
對方法使用 `async`/`Async` 關鍵字時，預期在該方法中的某處，也會使用 `await`/`Await` 關鍵字。  不過，若情況不是這樣，就會顯示快速動作，讓您可藉由移除 `async`/`Async` 關鍵字和變更傳回型別將方法設為同步。  使用 [快速動作] 功能表的 [將方法設為同步] 選項。

```CSharp
// Before
async Task<int> MyAsyncMethod()
{
    return 3;
}

// Make method synchronous

// After
int MyAsyncMethod()
{
    return 3;
}
```

```VB
' Before
Async Function MyAsyncMethod() As Task(Of Integer)
    Return 3
End Function

' Make method synchronous

' After
Function MyAsyncMethod() As Integer
    Return 3
End Function
```

### 將方法設為非同步
<a id="make-method-asynchronous" class="xliff"></a>
在方法內使用 `await`/`Await` 關鍵字時，預期方法本身會標記 `async`/`Async` 關鍵字。  不過，若情況不是這樣，就會顯示快速動作，讓您可以將方法設為非同步。  使用 [快速動作] 功能表的 [將方法/函式設為非同步] 選項。

```CSharp
// Before
int MyAsyncMethod()
{
    return await Task.Run(...);
}

// Make method synchronous

// After
async Task<int> MyAsyncMethod()
{
    return await Task.Run(...);
}
```

```VB
' Before
Function MyAsyncMethod() as Integer
    Return  Await Task.Run(...)
End Function

' Make method synchronous

' After
Async Function MyAsyncMethod() As Task(Of Integer)
    Return Await Task.Run(...)
End Function
```

### 移除不必要的 using/Import
<a id="remove-unnecesary-usingsimports" class="xliff"></a>
**移除不必要的 using/Import** 快速動作將會移除目前檔案中任何未使用的 `using` 和 `Import` 陳述式。  當您選取此項目時，將會立即移除未使用的命名空間匯入。

### 針對參考組件的類型、NuGet 套件的類型或您方案中的其他類型新增 using/Import
<a id="add-usingsimports-for-types-in-reference-assemblies-nuget-packages-or-other-types-in-your-solution" class="xliff"></a>
使用位於您方案中其他專案的類型會自動顯示快速動作，但是其他則需要從 [工具] > [選項] > [C#] 或 [基本] > [進階] 索引標籤啟用︰  

* 針對參考組件中的類型建議 using/Import
* 針對 NuGet 套件中的類型建議 using/Import

啟用時，如果您使用的類型位於目前未匯入，但存在於參考組件或 NuGet 套件的命名空間中，將會建立 using/Import 陳述式。

```CSharp
// Before
Debug.WriteLine("Hello");

// using System.Diagnostics;

// After
using System.Diagnostics;

Debug.WriteLine("Hello");
```

```VB
' Before
Debug.WriteLine("Hello")

' Imports System.Diagnostics

// After
Imports System.Diagnostics

Debug.WriteLine("Hello")
```

### 轉換成字串插值
<a id="convert-to-interpolated-string" class="xliff"></a>
[字串插值](/dotnet/csharp/language-reference/keywords/interpolated-strings)可以輕鬆表示含有內嵌變數的字串，類似於 **[String.Format](https://msdn.microsoft.com/library/system.string.format.aspx)** 方法。  這個快速動作會辨識字串串連或使用 **String.Format** 的情況，並將使用方式變更為字串插值。

```CSharp
// Before
int num = 3;
string s = string.Format("My string with {0} in the middle", num);

// Convert to interpolated string

// After
int num = 3;
string s = $"My string with {num} in the middle";
```

```VB
' Before
Dim num as Integer = 3
Dim s as String = String.Format("My string with {0} in the middle", num)

' Convert to interpolated string

' After
Dim num as Integer = 3
Dim s As String = $"My string with {num} in the middle"
```

### 移除合併衝突標記
<a id="remove-merge-conflict-markers" class="xliff"></a>
這些快速動作可讓您透過「採取變更」解決合併衝突，這樣會移除衝突的程式碼和標記。 (僅適用於 Visual Studio 2017 (15.3 版 - 預覽))。

![重構 - 解決合併衝突](~/docs/ide/media/vside-refactoring-merge-conflicts.png)

### 新增參數的 Null 檢查
<a id="add-null-checks-for-parameters" class="xliff"></a>
這個快速動作可讓您在程式碼中新增檢查，以判斷參數是否為 Null。 (僅適用於 Visual Studio 2017 (15.3 版 - 預覽))。

![重構 - 新增 Null 檢查](~/docs/ide/media/vside-refactoring-nullcheck.png)

### 建構函式產生器的增強功能
<a id="constructor-generator-improvements" class="xliff"></a>
當您建立建構函式時，這個快速動作可讓您選取要產生的屬性或欄位，或者您可以從空的內文產生建構函式。 您也可以使用它將參數從呼叫位置新增至現有的建構函式。 (僅適用於 Visual Studio 2017 (15.3 版 - 預覽))。

![重構 - 產生建構函式](~/docs/ide/media/vside-refactoring-constructors.png)

### 移除未使用的變數
<a id="remove-unused-variables" class="xliff"></a>
這個快速動作可讓您移除已宣告但從未在程式碼中使用的變數。 (僅適用於 Visual Studio 2017 (15.3 版 - 預覽))。

![重構 - 未使用的變數](~/docs/ide/media/vside-refactoring-unusedvars.png)

### 產生覆寫
<a id="generate-overrides" class="xliff"></a>
這個快速動作可讓您從類別或結構中的空白行建立覆寫。 [挑選成員] 對話方塊可讓您選擇要覆寫的成員。 (僅適用於 Visual Studio 2017 (15.3 版 - 預覽))。

![重構 - 覆寫](~/docs/ide/media/vside-refactoring-overrides.png)

![重構 - [覆寫] 對話方塊](~/docs/ide/media/vside-refactoring-overrides-dialog.png)

### 變更數值常值的基底
<a id="change-base-for-numeric-literals" class="xliff"></a>
這個快速動作可讓您將數值常值從一個基底數值系統轉換至另一個基底數值系統。 例如，您可以將數字變更為十六進位或二進位格式。 (僅適用於 Visual Studio 2017 (15.3 版 - 預覽))。

![重構 - 變更基底](~/docs/ide/media/vside-refactoring-changebase1.png)

![重構 - 變更基底](~/docs/ide/media/vside-refactoring-changebase2.png)

### 將數字分隔符號插入到常值中
<a id="insert-digit-separators-into-literals" class="xliff"></a>
這個快速動作可讓您將分隔符號字元加入到常值中。 (僅適用於 Visual Studio 2017 (15.3 版 - 預覽))。

![重構 - 變更數字分隔符號](~/docs/ide/media/vside-refactoring-separators.png)

### 將 **if** 建構轉換為 **switch**
<a id="convert-if-construct-to-switch" class="xliff"></a>
這個快速動作可讓您將 **if-then-else** 建構轉換為 **switch** 建構。 (僅適用於 Visual Studio 2017 (15.3 版 - 預覽))。

```CSharp
// Before
if (obj is string s)
{
  Console.WriteLine("obj is a string: " + s);  
}

else if (obj is int i && i > 10)
{
  Console.WriteLine("obj is an int greater than 10");
}

// Convert to switch

// After
switch (obj)
{
  case string s:
    Console.WriteLine("Obj is a string: " + s);
    break;
  case int i when i > 10:
    Console.WriteLine("obj is an int greater than 10");
    break;
}
```

```VB
' Before
If TypeOf obj Is String s Then
    Console.WriteLine("obj is a string: " + s)
Else If TypeOf obj Is Integer i And i > 10 Then
    Console.WriteLine("obj is an int greater than 10")
End If

' Convert to switch

' After
Select Case obj
  Case String s
    Console.WriteLine("Obj is a string: " + s)
    Exit Sub
  Case Integer i when i > 10
    Console.WriteLine("obj is an int greater than 10")
    Exit Sub
End Select
```

# 另請參閱
<a id="see-also" class="xliff"></a>
* [程式碼樣式及快速動作](code-styles-and-quick-actions.md)

