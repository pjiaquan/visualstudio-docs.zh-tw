---
title: "ActiveXObject 物件 (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "ActiveXObject"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ActiveXObject 物件"
  - "Automation 物件, ActiveXObject 物件"
ms.assetid: 9c7bed07-853f-48aa-92db-3131324746ec
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# ActiveXObject 物件 (JavaScript)
啟用及傳回對 Automation 物件的參考。  
  
 這個物件只用於具現化 Automation 物件，而且沒有任何成員。  
  
> [!WARNING]
>  這個物件是 Microsoft 擴充功能，只在 Internet Explorer 中才支援，[!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式中不支援。  
  
## 語法  
  
```  
  
newObj = new ActiveXObject(servername.typename[, location])  
```  
  
## 參數  
 `newObj`  
 必要項。  要對其指派 `ActiveXObject` 的變數名稱。  
  
 `servername`  
 必要項。  提供物件的應用程式名稱。  
  
 `typename`  
 必要項。  要建立之物件的類型或類別。  
  
 `location`  
 選擇項。  要在其中建立物件的網路伺服器名稱。  
  
## 備註  
 Automation 伺服器至少會提供一種類型的物件。  例如，文書處理應用程式可能會提供一個應用程式物件、一個文件物件和一個工具列物件。  
  
 您可以在 `HKEY_CLASSES_ROOT` 登錄機碼中識別主機電腦上的 `servername.typename` 值。  例如，以下提供一些可在該登錄機碼中找到的值範例，不過要視安裝的程式而定：  
  
-   Excel.Application  
  
-   Excel.Chart  
  
-   Scripting.FileSystemObject  
  
-   WScript.Shell  
  
-   Word.Document  
  
> [!IMPORTANT]
>  ActiveX 物件可能存在安全性問題。  若要使用 `ActiveXObject`，您可能需要在 Internet Explorer 中針對相關的安全性區域調整安全性設定。  例如，對於近端內部網路區域，您通常需要將自訂設定變更為 \[將未標示成安全的 ActiveX 控制項初始化並執行指令碼\]。  
  
 在沒有 Automation 物件的參考文件的情況下，若要識別可在程式碼中使用的 Automation 物件成員，您可能需要使用 COM 物件瀏覽器，例如 [OLE\/COM 物件檢視器](http://msdn.microsoft.com/library/d0kh9f4c.aspx)。  
  
 若要建立 Automation 物件，請將新的 `ActiveXObject` 指派給物件變數：  
  
```javascript  
var ExcelApp = new ActiveXObject("Excel.Application");  
var ExcelSheet = new ActiveXObject("Excel.Sheet");  
```  
  
 這個程式碼會啟動建立物件的應用程式 \(在這個案例中即為 Microsoft Excel 工作表\)。  一旦建立物件後，您就可以在程式碼中使用您定義的物件變數來參考它。  在下列範例中，您會使用物件變數 `ExcelSheet` 和其他的 Excel 物件 \(包括 Application 物件和 ActiveSheet.Cells 集合\) 存取新物件的屬性和方法。  
  
```javascript  
// Make Excel visible through the Application object.  
ExcelSheet.Application.Visible = true;  
// Place some text in the first cell of the sheet.  
ExcelSheet.ActiveSheet.Cells(1,1).Value = "This is column A, row 1";  
// Save the sheet.  
ExcelSheet.SaveAs("C:\\TEST.XLS");  
// Close Excel with the Quit method on the Application object.  
ExcelSheet.Application.Quit();  
```  
  
## 需求  
 在下列文件模式中可支援：Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準、Internet Explorer 8 標準、Internet Explorer 9 標準、Internet Explorer 10 標準、Internet Explorer 11 標準。  [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]應用程式不支援。  請參閱 [版本資訊](../../javascript/reference/javascript-version-information.md)。  
  
> [!NOTE]
>  [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] \(含\) 以後版本中不支援在遠端伺服器上建立 `ActiveXObject`。  
  
## 請參閱  
 [GetObject 函式](../../javascript/reference/getobject-function-javascript.md)   
 [運用 HTML5\/WCF 的強大功能進行唯一驗證範例應用程式](http://code.msdn.microsoft.com/Unique-Authentication-f32d2da0)