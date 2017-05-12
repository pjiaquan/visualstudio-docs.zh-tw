---
title: "GetObject 函式 (JavaScript) | Microsoft Docs"
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
  - "GetObject"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "GetObject 函式"
ms.assetid: 62efcdbc-8b86-491d-9000-ef38aa9942a9
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# GetObject 函式 (JavaScript)
從檔案中將參考傳回到一個 Automation 物件上。  
  
> [!NOTE]
>  Internet Explorer 9 \(標準模式\) 或更新版本不支援此函式。  
  
## 語法  
  
```  
GetObject([pathname] [, class])  
```  
  
## 參數  
 `pathname`  
 選擇項。  檔案的完整路徑和名稱包含要擷取的物件。  如果省略 `pathname`，則將需要 `class`。  
  
 `class`  
 選擇項。  物件的類別。  
  
 `class` 引數使用 `appname.objectype` 語法，並包含下列部分：  
  
 `appname`  
 必要項。  提供物件之應用程式的名稱。  
  
 `objectype`  
 必要項。  要建立之物件的型別或類別。  
  
## 備註  
 [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)] 或更新版本中不支援 `GetObject` 函式。  
  
 使用 `GetObject` 函式由某檔案中存取 Automation 物件。  將 `GetObject` 傳回的物件指派至該物件變數。  例如：  
  
```javascript  
var CADObject;  
CADObject = GetObject("C:\\CAD\\SCHEMA.CAD");  
```  
  
 在執行此段程式碼時，與指定之 `pathname` 相關聯的應用程式就會啟動，而且指定之檔案中的物件也會啟用。  如果 `pathname` 是長度為零的字串 \(""\)，則 `GetObject` 會傳回指定之型別的新物件執行個體。  如果省略 `pathname` 引數，則 `GetObject` 會傳回目前使用中的指定型別物件。  如果所指定型別的物件不存在，將會發生錯誤。  
  
 某些應用程式可讓您啟動檔案的一部分。  若要這樣做，請在檔案名稱後面加上驚嘆號 \(\!\)，並在其後加上所要啟動檔案部分的識別字串。  如需如何建立此一字串的資訊，請參閱建立該物件之應用程式的文件。  
  
 例如，繪圖應用程式中，檔案中儲存的圖形可能含有許多層。  您可以使用下列程式碼來啟動繪圖中命名為 `SCHEMA.CAD` 的圖層：  
  
```javascript  
var LayerObject = GetObject("C:\\CAD\\SCHEMA.CAD!Layer3");  
```  
  
 如果不指定物件的類別，Automation 會根據您所提供的檔案名稱來決定要啟動的應用程式和啟用的物件。  不過，某些檔案可以支援一種以上物件類別。  例如，繪圖可能會支援三個不同的物件型別：Application 物件、Drawing 物件和 Toolbar 物件，它們都是相同檔案的一部分。  若要指定檔案中要啟動的物件，請使用選擇性的 `class` 引數。  例如：  
  
```javascript  
var MyObject;  
MyObject = GetObject("C:\\DRAWINGS\\SAMPLE.DRW", "FIGMENT.DRAWING");  
```  
  
 在前述範例中，`FIGMENT` 是繪圖應用程式的名稱，而 `DRAWING` 是其支援的一種物件型別。  物件一旦啟動後，您就可以使用您定義的物件變數以代碼參考它。  在先前的例子中，可使用物件變數 `MyObject` 來存取新物件的屬性和方法。  例如：  
  
```javascript  
MyObject.Line(9, 90);  
MyObject.InsertText(9, 100, "Hello, world.");  
MyObject.SaveAs("C:\\DRAWINGS\\SAMPLE.DRW");  
```  
  
> [!NOTE]
>  當物件目前有執行個體，或您想用已載入的檔案建立物件，可使用 `GetObject` 函式。  如果目前沒有執行個體，而且不希望物件由一個已載入的檔案啟動，請使用 `ActiveXObject` 物件。  
  
 如果一個物件已將本身登錄為單一執行個體物件，無論 `ActiveXObject` 執行幾次，該物件也只能建立一個執行個體。  對於單一執行個體的物件，使用長度為零的字串 \(""\) 語法呼叫 `GetObject` 時，永遠會傳回相同的執行個體，如果省略 `pathname` 引數，則會造成錯誤。  
  
## 需求  
 下列文件模式有提供支援：Quirks、Internet Explorer 6 標準、Internet Explorer 7 標準和 Internet Explorer 8 標準。  請參閱 [版本資訊](../../javascript/reference/javascript-version-information.md)。  
  
## 請參閱  
 [ActiveXObject 物件](../../javascript/reference/activexobject-object-javascript.md)