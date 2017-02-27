---
title: "全域 Windows Form 和 Web Form 的文化特性特定類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "全球化 [Windows Forms], 類別"
  - "Web 應用程式 [.NET Framework], 全球化"
  - "文化特性, 文化特性專用類別"
  - "數字, 國際化"
  - "當地語系化 [Windows Form], 類別"
  - "全球化 [Visual Studio], 文化特性專用類別"
  - "Windows Forms, 當地語系化"
  - "國際應用程式 [Visual Studio], 資料格式"
  - "時間 [Visual Studio], 國際化"
  - "日期 [Visual Studio], 國際化"
  - "文化特性"
  - "國際字元"
  - "貨幣格式"
  - "ASP.NET, 全球化"
  - "類別 [Visual Studio], 文化特性專用"
  - "當地語系化 [Visual Studio], 文化特性專用類別"
ms.assetid: 0d06a0a4-f887-4f7c-bde7-1d543c06f803
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# <a name="culture-specific-classes-for-global-windows-forms-and-web-forms"></a>全域 Windows Form 和 Web Form 的文化特性特定類別
每個文化特性對於顯示日期、時間、數字、貨幣及其他資訊都有不同的慣例。 <xref:System.Globalization> 命名空間包含的類別可用來修改特定文化特性顯示值的方式，例如 <xref:System.Globalization.DateTimeFormatInfo>、**Calendar** 和 <xref:System.Globalization.NumberFormatInfo>。  
  
## <a name="using-the-culture-setting"></a>使用文化特性設定  
 但大部分的情況，您會使用文化特性設定 (儲存於應用程式或控制台的 [地區選項] 中) 自動在執行階段判斷慣例並據以格式化資訊。 如需設定文化特性的詳細資訊，請參閱[如何：設定 Windows Form 全球化的文化特性和 UI 文化特性](http://msdn.microsoft.com/en-us/694e049f-0b91-474a-9789-d35124f248f0)或[如何：為 ASP.NET 網頁全球化設定文化特性和 UI 文化特性](http://msdn.microsoft.com/Library/76091f86-f967-4687-a40f-de87bd8cc9a0)。 根據文化特性設定自動格式化資訊的類別，稱為文化特性專用。 某些特定文化特性的方法是 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>、<xref:System.Console.WriteLine%2A?displayProperty=fullName> 和 <xref:System.String.Format%2A?displayProperty=fullName>。 一些文化特性函式 (在 Visual Basic 語言中) 如 `MonthName` 和 `WeekDayName`。  
  
 例如，下列程式碼示範如何使用 <xref:System.IFormattable.ToString%2A> 方法以針對目前文化特性來格式化貨幣：  
  
```vb#  
' Put the Imports statements at the beginning of the code module  
Imports System.Threading  
Imports System.Globalization  
' Display a number with the culture-specific currency formatting  
Dim MyInt As Integer = 100  
Console.WriteLine(MyInt.ToString("C", Thread.CurrentThread.CurrentCulture))  
  
```  
  
```c#  
// Put the using statements at the beginning of the code module  
using System.Threading;  
using System.Globalization;  
// Display a number with the culture-specific currency formatting  
int myInt = 100;  
Console.WriteLine(myInt.ToString("C", Thread.CurrentThread.CurrentCulture));  
```  
  
 如果文化特性設定為 "fr-FR"，您會在輸出視窗中看到這個：  
  
 `100,00`  
  
 如果文化特性設定為 "en-US"，您會在輸出視窗中看到這個：  
  
 `$100.00`  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IFormattable.ToString%2A?displayProperty=fullName>   
 <xref:System.Globalization.DateTimeFormatInfo>   
 <xref:System.Globalization.NumberFormatInfo>   
 <xref:System.Globalization.Calendar>   
 <xref:System.Console.WriteLine%2A?displayProperty=fullName>   
 <xref:System.String.Format%2A?displayProperty=fullName>   
 [全球化和當地語系化應用程式](../ide/globalizing-and-localizing-applications.md)


<!--HONumber=Feb17_HO4-->


