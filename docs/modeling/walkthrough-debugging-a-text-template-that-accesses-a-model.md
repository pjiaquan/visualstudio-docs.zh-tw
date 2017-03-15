---
title: "逐步解說︰ 偵錯文字範本存取模型 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 6
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 7bbe2b592dc315bc0885e1f1ca4c890e4e66255d
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>逐步解說：偵錯存取模型的文字範本
當您修改或加入定義域專屬語言方案中的文字範本時，您可能會發生錯誤時，引擎會轉換原始碼，或在編譯時產生的程式碼的範本。 下列逐步解說會示範一些您可以進行偵錯文字範本的操作。  
  
> [!NOTE]
>  如需文字範本一般情況下，請參閱[程式碼產生和 T4 文字範本](../modeling/code-generation-and-t4-text-templates.md)。 如需有關偵錯文字範本的詳細資訊，請參閱[逐步解說︰ 偵錯文字範本](http://msdn.microsoft.com/Library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f)。  
  
## <a name="creating-a-domain-specific-language-solution"></a>建立定義域專屬語言方案  
 在此程序，您可以建立定義域專屬語言方案具有下列特性︰  
  
-   名稱︰ DebuggingTestLanguage  
  
-   方案範本︰ 最小語言  
  
-   檔案副檔名︰.ddd  
  
-   公司名稱︰ Fabrikam  
  
 如需建立定義域專屬語言方案的詳細資訊，請參閱[How to︰ 建立定義域專屬的語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。  
  
## <a name="creating-a-text-template"></a>建立文字範本  
 將文字範本加入至您的方案。  
  
#### <a name="to-create-a-text-template"></a>若要建立文字範本  
  
1.  建置方案並開始偵錯工具中執行。 (在**建置** 功能表上，按一下 **重建方案**，然後在**偵錯** 功能表上，按一下**開始偵錯**。)Visual Studio 的新執行個體開啟偵錯專案。  
  
2.  新增名為文字檔`DebugTest.tt`偵錯專案。  
  
3.  請確定**自訂工具**DebugTest.tt 屬性設定為`TextTemplatingFileGenerator`。  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>偵錯從文字範本存取模型的指示詞  
 您可以從文字範本中的運算式與陳述式，存取模型之前，您必須先呼叫產生指示詞處理器。 呼叫產生指示詞處理器可讓類別模型中的文字範本程式碼能夠做為屬性。 如需詳細資訊，請參閱[文字範本存取模型](../modeling/accessing-models-from-text-templates.md)。  
  
 下列程序，您將偵錯的指示詞的名稱不正確和不正確的屬性名稱。  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>若要偵錯的指示詞的名稱不正確  
  
1.  下列程式碼來取代 DebugTest.tt 中的程式碼︰  
  
    > [!NOTE]
    >  包含錯誤的程式碼。 您引用的錯誤以進行偵錯。  
  
    ```c#  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb#  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  在**方案總管 中**DebugTest.tt，以滑鼠右鍵按一下，然後按**執行自訂工具**。  
  
     **錯誤清單** 視窗會顯示此錯誤︰  
  
     **名為 'DebuggingTestLanguageDirectiveProcessor' 處理器不支援名為 'modelRoot' 指示詞。將不會執行轉換。**  
  
     在此情況下，指示詞的呼叫中包含的指示詞的名稱不正確。 您已指定`modelRoot`因為指示詞的名稱，但正確指示詞的名稱是`DebuggingTestLanguage`。  
  
3.  按兩下中的錯誤**錯誤清單**跳至程式碼的視窗。  
  
4.  若要修正此程式碼，此指示詞名稱變更為`DebuggingTestLanguage`。  
  
     變更會反白顯示。  
  
    ```c#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb#  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  在**方案總管 中**DebugTest.tt，以滑鼠右鍵按一下，然後按**執行自訂工具**。  
  
     現在系統轉換文字範本，並產生對應的輸出檔。 將不會看到的任何錯誤都**錯誤清單**視窗。  
  
#### <a name="to-debug-an-incorrect-property-name"></a>若要偵錯不正確的屬性名稱  
  
1.  下列程式碼來取代 DebugTest.tt 中的程式碼︰  
  
    > [!NOTE]
    >  包含錯誤的程式碼。 您引用的錯誤以進行偵錯。  
  
    ```c#  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb#  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  在**方案總管 中**DebugTest.tt，以滑鼠右鍵按一下，然後按**執行自訂工具**。  
  
     **錯誤清單** 視窗隨即出現並顯示這些錯誤之一︰  
  
     (C#)  
  
     **正在編譯轉換︰ Microsoft.VisualStudio.TextTemplating\<GUID >。GeneratedTextTransformation' 未包含 'ExampleModel' 的定義**  
  
     (Visual Basic)  
  
     **正在編譯轉換: 'ExampleModel' 不是成員的 ' Microsoft.VisualStudio.TextTemplating\<GUID >。GeneratedTextTransformation'。**  
  
     在此情況下，文字範本程式碼包含不正確的屬性名稱。 您已指定`ExampleModel`做為屬性名稱，但正確的屬性名稱是`LibraryModel`。 您可以找到正確的屬性名稱中提供參數，如下列程式碼所示︰  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  按兩下 [錯誤清單] 視窗，跳至程式碼中的錯誤。  
  
4.  若要修正此程式碼，將屬性名稱變更為`LibraryModel`文字範本程式碼中。  
  
     所做的變更會反白顯示。  
  
    ```c#  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.LibraryModel #>  
    <#  
    foreach (ExampleElement element in this.LibraryModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb#  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.LibraryModel #>  
    <#  
    For Each element as ExampleElement in Me.LibraryModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
5.  在**方案總管 中**DebugTest.tt，以滑鼠右鍵按一下，然後按**執行自訂工具**。  
  
     現在系統轉換文字範本，並產生對應的輸出檔。 將不會看到的任何錯誤都**錯誤清單**視窗。
