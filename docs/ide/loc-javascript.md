---
title: "&lt;loc&gt; (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "loc JavaScript XML 標記"
  - "loc JavaScript XML 標記"
ms.assetid: 0d3349b6-4bdd-418f-bc11-73665305baae
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# &lt;loc&gt; (JavaScript)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

對提供當地語系化 IntelliSense資訊的附屬檔案，指定它的位置和型別。  
  
## 語法  
  
```  
<loc filename="filename"  
    format="vsdoc|messagebundle" />  
```  
  
#### 參數  
 `filename`  
 選擇項。  包含中性文化特性的當地語系化資訊之附屬檔案的根目錄名稱。  當 Visual Studio 搜尋關於當地語系化資訊時，它會嘗試找出這個檔案的文化特性特定版本。  舉例來說，如果`filename`為jquery.xml，則Visual Studio會在包含 `<loc>` 項目的.js 檔案的相同位置上，搜尋正確的文化特性資料夾\(例如 JA\)。  如果找到這個文化特性資料夾，它會檢查 jquery.xml 檔案是否存在於此。  如果找不到正確的檔案，它反而會使用 Managed 資源位置規則。  `filename` 的預設值是目前檔案的名稱，但副檔名為.xml 而非 .js。  
  
 `format`  
 選擇項。  用於當地語系化的附屬檔案類型。  請使用 `messagebundle` 指定由Open Ajax 中繼資料所定義的訊息繫結之用途。  建議格式是`messagebundle`。  不過，這種格式不支援於Microsoft Ajax 或在 .winmd 檔案中。  請使用 `vsdoc` 指定 Microsoft Ajax 與 Windows 執行階段所使用的標準 .NET Framework 當地語系化格式。  這是一個選擇性的屬性。  預設格式為 `vsdoc`。  
  
## 備註  
 `<loc>` 項目必須出現在檔案頂端，和 `<reference>` 項目相同的部分。  `<loc>` 項目的使用方式規則同於 `<reference>` 項目。  如需詳細資訊，請參閱 [JavaScript IntelliSense](../ide/javascript-intellisense.md) 中的｢參考指令｣一節。  
  
 Visual Studio 管理每個 .js 檔案的單一 `<loc>` 項目。  如果目前有多個 `<loc>` 項目，則只會使用單一 `<loc>` 項目。  判斷要使用哪種 `<loc>` 項目的行為尚未定義。  
  
 在使用訊息繫結格式時，請在 XML 文件註解中使用 `locid` 屬性以指定 `name` 屬性值。  
  
## 範例  
 下列範例示範如何以messagebundle格式使用`<loc>`項目。  將下列 XML 加入至名為 messageFilename.xml 的檔案，並將檔案放在正確的文化特性資料夾，就像在 `filename` 參數的描述中所指定的那樣。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<messagebundle>  
  <msg name="1">A class that represents a rectangle</msg>  
  <msg name="2">The height of a rectangle</msg>  
  <msg name="3">The width of a rectangle</msg>  
</messagebundle>  
  
```  
  
 以messagebundle範例來說，加入下列程式碼至專案中的JavaScript 檔案：  `<loc>` 元素必須出現為JavaScript 檔案中的第一行。  如果可行的話，此程式碼的描述將由當地語系化描述所取代。  
  
```javascript  
/// <loc filename="messageFilename.xml" format="messagebundle"/>  
  
function doSomething(a,b)   
{  
    /// <summary locid='1'>description</summary>  
    /// <param name='a' locid='2'>parameter a description</param>  
    /// <param name='b' locid='3'>parameter b description</param>  
}  
  
```  
  
 下列範例使用 VSDoc 格式。  將下列 XML 加入至名為 scriptFilename.xml 的檔案，並將檔案放在正確的文化特性資料夾。  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<doc>  
  <assembly>  
    <name>Lights</name>  
  </assembly>  
  <members>  
    <member name="M:illuminate">  
      <summary>Activates a light. </summary>  
      <param name='a'>The light to activate. </param>  
    </member>  
  </members>  
</doc>  
  
```  
  
 以VSDoc範例來說，加入下列程式碼至專案中的JavaScript 檔案：  如果可行的話，此程式碼的描述將由當地語系化描述所取代。  
  
```javascript  
/// <loc filename="scriptFilename.xml" format="vsdoc" />  
  
function illuminate(a)   
{  
    /// <summary locid='M:illuminate'>description</summary>  
    /// <param name='a' type='Number'>parameter a description</param>  
}  
  
```  
  
## 請參閱  
 [XML 文件註解](../ide/xml-documentation-comments-javascript.md)