---
title: "支援的網站範本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "我們在網站專案範本"
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 支援的網站範本
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]網站專案範本和項目範本會提供可重複使用且可自訂的網站專案和項目 stub，進而加速開發程序，藉由移除不必從頭開始建立新的網站專案和項目。  如需有關[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]範本，請參閱[建立自訂專案與項目範本](../../ide/creating-project-and-item-templates.md)。  
  
## 專案範本的資料夾  
 網站專案範本範本通常會安裝 *Visual Studio 的安裝路徑* \\Common7\\IDE\\ProjectTemplates\\Web\\，每一個的 web 程式設計語言來命名的子資料夾中。  
  
## 專案檔  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]整合式的開發環境 \(IDE\) 需要用來將範本對應至正確的專案類型的專案檔案的副檔名。  Web 專案沒有專案檔，因為空的專案檔案的副檔名.webproj 係授與支援。  
  
 語言名稱字串，選擇性地加入範本中，讓 Web 專案系統設定語言預設**加入新項目**範本為基礎的項目\] 對話方塊。  字串必須是該檔案的第一行，而且必須符合在 AddItemLanguageName 下登錄中的 Intellisense 引擎註冊的名稱，以及專案 Subtype\(VsTemplate\) 下註冊的名稱。  如需詳細資訊，請參閱 [網站支援屬性](../../extensibility/internals/web-site-support-attributes.md)。  
  
 如果字串不存在，Web 專案系統會嘗試判斷 Web 專案樣板加入的專案範本的網頁的語言屬性和檔案副檔名為基礎的預設語言。  
  
## 專案範本  
 網站專案範本用來建立新的 Web 站台，以回應**新的 Web 站台** 命令 **檔案**功能表。  目前支援的三個網站專案類型：  
  
-   空的網站專案  
  
-   網站專案  
  
-   Web 服務專案  
  
### 空的網站專案  
 這些檔案會建立新的空白網站以回應**空的 Web 站台** 命令，即可以使用後指向 **新的 Web 站台** 上 **檔案**功能表：  
  
-   EmptyWeb.vstemplate  
  
     輔助線建立新的空白網站的範本檔案。  
  
-   EmptyWeb.webproj  
  
     這是系統的檔案所造成的專案範本。  它會滿足 EmptyWeb.vstemplate 檔案中的專案檔案參考。  
  
### 網站專案  
 這些檔案建立新的網站，以回應 **ASP。NET 網站** 命令，即可以使用後指向 **新的 Web 站台** 上 **檔案**功能表：  
  
-   Default.aspx  
  
     新的 Web 站台預設首頁。  語言屬性會指定程式碼後置語言的一部分，且 CodeFile 屬性指定包含此網頁相關聯的程式碼後置程式碼的相依檔案。  
  
-   Default.aspx。*延伸模組*  
  
     包含預設的 \[首頁\] 頁面的程式碼後置程式碼的相依檔案。  程式碼後置語系會決定*副檔名*這個檔案。  
  
-   web.config  
  
     根 web.site 組態檔中。  
  
-   WebApplication.vstemplate  
  
     對於判斷網站方案的內容，並強制 \[App\_Data\] 資料夾建立的範本檔案。  
  
-   WebApplication.webproj  
  
     這是系統的檔案所造成的專案範本。  它會滿足 WebApplication.vstemplate 檔案中的專案檔案參考。  
  
### Web 服務專案  
 這些檔案建立新的網站，以回應 **ASP。NET Web 服務** ，晚指到可用的命令 **新的 Web 站台** 的 **檔案**功能表：  
  
-   \] 的 service.asmx 上  
  
     新的 Web 服務的 HTML 頁面。  語言屬性會指定程式碼後置語言的一部分，且程式碼後置屬性指定包含這項服務相關聯的程式碼後置程式碼的相依檔案。  
  
-   服務。 *延伸模組*  
  
     實作服務類別的相依檔案。  程式碼後置語系會決定*副檔名*這個檔案。  
  
-   web.config  
  
-   根 web.site 組態檔中。  
  
-   WebService.vstemplate  
  
     對於判斷網站方案的內容，並強制 \[App\_Data\] 和 \[App\_Code 資料夾建立的範本檔案。  服務。*副檔名*檔案會複製到 \[App\_Code\] 資料夾中的色彩。  
  
-   WebService.webproj  
  
     這是系統的檔案所造成的專案範本。  它會滿足 WebService.vstemplate 檔案中的專案檔案參考。  
  
## 專案項目範本的資料夾  
 Web 專案項目樣板通常安裝範本在 *Visual Studio 的安裝路徑* \\Common7\\IDE\\ItemTemplates\\Web\\，它的 web 程式設計語言來命名的子資料夾中的每一個。  
  
## 專案項目範本  
 網站專案項目範本用來將新的 Web 網頁加入至網站，以回應**加入現有項目**指令。  這類的 Web 網頁是目前支援：  
  
-   新的類別  
  
-   新的 HTML 網頁  
  
-   新的 Web 表單  
  
-   新的主版頁面  
  
### 新的類別  
 此範本會建立新的原始程式檔定義一個空白的類別，以回應**加入新的類別**指令。  
  
-   類別。 *延伸模組*  
  
     原始程式檔實作空的類別。  程式碼後置語系會決定*副檔名*這個檔案。  
  
-   Class.vstemplate  
  
     對於建立原始程式檔，並判斷其內容的範本檔案。  
  
### 新的 HTML 網頁  
 這個範本建立新的 Web 網頁，以回應**加入新的 HTML 網頁**指令。  
  
-   HTMLPage.htm  
  
     起始網頁的內容。  這個網頁通常會有任何相關聯的程式碼後置的相依檔案。  若要建立一個智慧、 網頁相關聯的程式碼後置檔案，改用 \[網頁表單範本。  
  
-   HTMLPage.vstemplate  
  
     對於建立 Web 網頁，並判斷其內容的範本檔案。  
  
### 新 WebForm  
 這個範本建立新的智慧型 Web 網頁，以回應**加入新的 Web Form** 指令。  
  
 若要建立相依的程式碼後置原始程式檔，請選取 \[ **程式碼置於個別檔案**。  否則，會建立具有空白的指令碼區塊，並沒有 \< %%\> 單一 Web 網頁 連結的相依檔案的指示詞。  
  
 若要建立選取的主版頁面的內容頁面，請選取 \[ **選取主版頁面**。  
  
-   WebForm.aspx  
  
     起始網頁的內容。  這個 Web 網頁是沒有相關聯的程式碼後置的相依檔案。  
  
-   WebForm\_cb.aspx  
  
     起始網頁的內容。  這個網頁有關聯的程式碼後置相依檔。  
  
-   程式碼後置。 *延伸模組*  
  
     實作 webform 類別的相依檔案。  程式碼後置語系會決定*副檔名*這個檔案。  
  
-   ContentPage.aspx  
  
     起始網頁做為內容頁面的內容。  這個 Web 網頁是沒有相關聯的程式碼後置的相依檔案。  
  
-   ContentPage\_cb.aspx  
  
     起始網頁做為內容頁面的內容。  這個網頁有關聯的程式碼後置相依檔。  
  
-   WebForm.vstemplate  
  
     範本檔案，以判斷新的 web 網頁和其相依的檔案的內容，如果有的話。  
  
### 新增主版頁面  
 這個範本建立新的主版頁面，以回應**加入新的主版頁面**指令。  
  
 若要建立相依的程式碼後置原始程式檔，請選取 \[ **程式碼置於個別檔案**。  否則，會建立具有空白的指令碼區塊，並沒有 \< %%\> 單一 Web 網頁 連結的相依檔案的指示詞。  
  
-   MasterPage.master  
  
     主版頁面開始的內容。  此主版頁面會有任何相關聯的程式碼後置的相依檔案。  
  
-   MasterPage\_cb.master  
  
     主版頁面開始的內容。  此主版頁面會有相關聯的程式碼後置相依檔。  
  
-   程式碼後置。*延伸模組*  
  
     實作的主版頁面類別的相依檔案。  程式碼後置語系會決定*副檔名*這個檔案。  
  
-   MasterPage.vstemplate  
  
     範本檔案，以判斷新的主版頁面和其相依的檔案的內容，如果有的話。  
  
## 請參閱  
 [網站支援](../../extensibility/internals/web-site-support.md)