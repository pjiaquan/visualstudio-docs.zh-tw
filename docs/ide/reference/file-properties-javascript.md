---
title: "JavaScript、檔案屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "javascript.project.property.expandedsdknode.fileversion"
  - "javascript.project.property.expandedsdknode.uri"
  - "javascript.project.property.expandedsdknode.filename"
  - "javascript.project.property.reference.description"
  - "javascript.project.property.reference.specificversion"
  - "javascript.project.property.reference.identity"
  - "javascript.project.property.fullpath"
  - "javascript.project.property.packageaction"
  - "javascript.project.property.reference.package"
  - "javascript.project.property.copytooutputdirectory"
  - "javascript.project.property.expandedsdknode.sdkpath"
  - "javascript.project.property.reference.filetype"
  - "javascript.project.property.reference.culture"
  - "javascript.project.property.filename"
  - "javascript.project.property.reference.resolvedpath"
  - "javascript.project.property.reference.version"
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
caps.latest.revision: 7
caps.handback.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# JavaScript、檔案屬性
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以使用檔案屬性來表示專案系統應對檔案執行的動作。  例如，您可以設定檔案屬性來表示是否應該將檔案加入至封裝為資源檔。  
  
 您可以在 \[方案總管\] 中選取任何檔案，接著在 \[屬性\] 視窗中檢查它的屬性。  JavaScript 檔案有四個屬性: \[**複製到輸出目錄**\]、 \[**包裝動作**\]、 \[**檔案名稱**\] 和 \[**檔案路徑。**\]。  
  
## 檔案屬性  
 本節說明屬性通用的 JavaScript 檔案。  
  
### 複製到輸出目錄屬性  
 這個屬性會指定在哪些情況下要將選取的原始程式檔 \(Source File\) 複製到輸出目錄中。  如果永遠不要將檔案複製到輸出目錄中，請選取 \[**不要複製**\]。  如果一定要將檔案複製至輸出目錄中，請選取 \[**永遠複製**\]。  如果只要在當檔案比輸出目錄中同名的現有檔案更新時才複製，請選取 \[**有更新時才複製**\]。  
  
### 封裝動作  
 \[**封裝動作**\] 屬性會指出， Visual Studio 對檔案執行組建時  \[**封裝動作**\] 可能有下列任一值:  
  
-   \[**無**\] \-檔案封裝資訊清單中不包含。  範例之一是包含文件的文字檔，例如讀我檔案。  
  
-   \[**內容**\] \-檔案在套件資訊清單中。  例如，這個設定是 .htm、.js、.css、影像、音訊或視訊檔案的預設值。  
  
-   \[**資訊清單**\] –檔案封裝資訊清單中不包含。  相反地，當，會產生套件資訊清單時，檔案用於輸入。  這是 package.appxmanifest 檔案的預設值。  
  
-   \[**資源**\] \-檔案封裝資訊清單中不包含。  相反地，檔案內容在進入套件資訊清單的封裝資源索引 \(PRI\) 索引。  這個值通常用於資源檔。  
  
 \[**封裝動作**\] 的預設值需視您加入方案的檔案的副檔名。  
  
### 檔名屬性  
 顯示檔案名稱做為唯讀值。  若要重新命名檔案，您可以在方案總管中必須以滑鼠右鍵並選取 \[ \[**重新命名**\]。  
  
### 完整路徑屬性  
 顯示檔案的完整路徑做為唯讀值。  若要變更檔案的路徑，您可以拖放在方案總管中的檔案。  
  
## 參考文件屬性  
 本節說明屬性通用從 [!INCLUDE[win8_app_js](../../ide/reference/includes/win8_app_js_md.md)]參考的檔案。  當您選取之類的參考 .winmd 檔案，一 SDK 參考、專案對專案間的參考或組件參考在方案總管中，其他屬性在 \[屬性\] 視窗可能會顯示，根據檔案類型。  
  
### 文化特性  
 顯示語言與參考。  
  
### 檔案類型  
 顯示參考的檔案類型。  
  
### 檔案版本  
 顯示參考的檔案版本。  
  
### 識別  
 顯示使用於專案中，專案檔儲存參考的識別。  
  
### 封裝  
 顯示封裝資訊清單的名稱與參考。  
  
### 已解析的路徑。  
 顯示路徑用於專案的參考。  
  
### SDK 的路徑。  
 顯示路徑的 SDK 參考檔案。  
  
### Uri  
 顯示專案中的 HTML 或 JavaScript 檔案必須包括檔案做為原始程式檔的 URI。  
  
### 版本  
 顯示參考的版本。  
  
## 請參閱  
 [NIB: Project Properties \(Visual Studio\)](http://msdn.microsoft.com/zh-tw/eb4c97ed-f667-4850-98d0-6e2a4d21bbca)