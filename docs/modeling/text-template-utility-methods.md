---
title: "文字範本公用程式方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "文字範本, 公用程式方法"
ms.assetid: 8c11f9f7-678b-4f0c-b634-dc78fda699d1
caps.latest.revision: 50
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 50
---
# 文字範本公用程式方法
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

撰寫 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 文字範本中的程式碼時，您隨時都有許多方法可用。  這些方法會在 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> 中定義。  
  
> [!TIP]
>  在一般 \(未經前置處理過的\) 文字範本中，您也可以使用主應用程式環境所提供的方法和屬性。  例如，您可以解析檔案路徑、記錄錯誤，以及取得 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 提供的服務和任何載入的封裝。  如需詳細資訊，請參閱[Accessing Visual Studio from a Text Template](http://msdn.microsoft.com/zh-tw/0556f20c-fef4-41a9-9597-53afab4ab9e4)。  
  
## 寫入方法  
 您可以使用 `Write()` 和 `WriteLine()` 方法，將文件附加在標準程式碼區塊中，而不使用運算式程式碼區塊。  下列兩行程式碼區塊的功能相同。  
  
##### 含有程式碼區塊的運算式區塊  
  
```  
<#  
int i = 10;  
while (i-- > 0)  
    { #>  
        <#= i #>  
    <# }  
#>  
```  
  
##### 使用 WriteLine\(\) 的程式碼區塊  
  
```  
<#   
    int i = 10;  
    while (i-- > 0)  
    {   
        WriteLine((i.ToString()));  
    }  
#>  
```  
  
 您可能會發覺，與其在包含巢狀控制結構的冗長程式碼區塊中使用運算式區塊，還不如使用上述其中一個公用程式方法來得好用。  
  
 `Write()` 和 `WriteLine()` 方法有兩個多載，一個會接受單一字串參數，而另一個則接受複合格式字串加上要包含在字串內之物件的陣列 \(類似 `Console.WriteLine()` 方法\)。  下列兩個 `WriteLine()` 的用法在功能上相同：  
  
```  
<#  
    string msg = "Say: {0}, {1}, {2}";  
    string s1 = "hello";  
    string s2 = "goodbye";  
    string s3 = "farewell";  
  
    WriteLine(msg, s1, s2, s3);  
    WriteLine("Say: hello, goodbye, farewell");  
#>   
```  
  
## 縮排方法  
 您可以使用縮排方法將文字範本的輸出格式化。  <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation> 類別具有 `CurrentIndent` 字串屬性 \(可在文字範本中顯示目前的縮排\) 以及 `indentLengths` 欄位 \(已加入的縮排清單\)。  您可以使用 `PushIndent()` 方法加入縮排，以及使用 `PopIndent()` 方法將縮排去除。  如果您想要移除所有縮排，請使用 `ClearIndent()` 方法。  下列程式碼區塊會示範這些方法的使用方式：  
  
```  
<#  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
    ClearIndent();  
    WriteLine(CurrentIndent + "Hello");  
    PushIndent("    ");  
    WriteLine(CurrentIndent + "Hello");  
#>  
```  
  
 這個程式碼區塊會產生下列輸出：  
  
```  
Hello  
        Hello  
                Hello  
Hello  
        Hello  
```  
  
## 錯誤和警告方法  
 您可以使用錯誤及警告公用程式方法，將訊息加入至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的 \[錯誤清單\]。  例如，下列程式碼會將錯誤訊息加入至 \[錯誤清單\]：  
  
```  
<#  
  try  
  {  
    string str = null;  
    Write(str.Length.ToString());  
  }  
  catch (Exception e)  
  {  
    Error(e.Message);  
  }  
#>    
```  
  
## 存取主應用程式和服務提供者  
 `this.Host` 屬性可用來存取要執行範本之主應用程式所公開的屬性。  若要使用 `this.Host`，您必須在 `<@template#>` 指示詞中設定 `hostspecific` 屬性：  
  
 `<#@template ...  hostspecific="true" #>`  
  
 `this.Host` 的型別視要執行範本之主應用程式的型別而定。  在於 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中執行的範本內，您可以將 `this.Host` 的型別轉換為 `IServiceProvider`，以存取像 IDE 這類服務。  例如：  
  
```  
EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
```  
  
## 使用不同的公用程式方法集  
 範本檔會在文字產生流程當中轉換成類別，這個類別一律命名為 `GeneratedTextTransformation` 而且會繼承 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。  如果您想要改用其他方法集，可以撰寫自己的類別，然後在範本指示詞中指定這個類別。  您的類別必須繼承 <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation>。  
  
```  
<#@ template inherits="MyUtilityClass" #>  
```  
  
 請使用 `assembly` 指示詞來參考已編譯之類別所在的組件。