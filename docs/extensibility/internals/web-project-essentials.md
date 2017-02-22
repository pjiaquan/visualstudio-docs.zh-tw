---
title: "Web 專案的基本資訊 | Microsoft Docs"
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
  - "web 專案 essentials"
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Web 專案的基本資訊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Web 專案建立 Web 應用程式。 您可以使用 Web 專案建立 Web 應用程式，有智慧的網頁。 智慧型的網頁有呈現網頁上指定的伺服器端程式碼。  
  
 使用傳統的程式設計語言，例如 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 或 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], ，您可以建立智慧型網頁，以收集和處理來自使用者的資訊、 將它儲存在資料庫中，等等。  
  
-   程式碼後置模型會將相依的原始程式碼檔案擁有.asmx 的檔案副檔名.aspx 網頁關聯。 例如，hello.aspx 可能有相依的原始碼檔案 hello.aspx.cs。  
  
-   智慧型網頁相關聯的伺服器端程式碼會編譯為可執行檔位於網站的 /bin 資料夾中。  
  
-   其他來源的程式碼檔案，例如與特定網頁的 helper 類別位於網站 /App_Code 資料夾中。  
  
    -   網站專案 (WSP) 會產生一個可執行檔，每個智慧網頁。 其他可執行檔會產生從任何的原始程式碼檔案存放在 /App_Code 資料夾中。  
  
    -   Web 應用程式專案 (WAP) 會產生單一的可執行檔，結合了所有智慧型的網頁，以及在 /App_Code 資料夾中的所有原始程式檔的程式碼。  
  
-   Web 專案的方案檔位於與網站本身分開。 根據預設，方案檔位於 \Documents and 設定\\*YourAccount*\My 文件\\*\< Visual Studio # # # >*\Projects\\*YourWebSite*。  
  
    > [!NOTE]
    >  如果您想要保留與網站的方案檔，只需將那里，並重新開啟它。  
  
-   如果您開啟網站，Visual Studio 中沒有方案檔時，新的方案檔會自動產生它。  
  
-   Web 專案的任何專案檔。 專案資訊會儲存在方案檔、 web.config 檔案中，和其他位置。  
  
-   將全域屬性加入至 Web 專案會自動在 Web 專案的方案資料夾中建立儲存體檔案。  
  
-   智慧型網頁可以是藉由使用 Page 指示詞相關聯的伺服器端程式設計語言或 \< 指令碼 runat ="server"> 標記。  
  
-   此外，網頁可以有任意任何的數目指令碼語言撰寫的用戶端指令碼區塊。  
  
-   藉由加入專案和項目範本和註冊，以實作網站專案系統 [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] 專案。  
  
-   WAP 系統會實作為專案子型別，也稱為專案類別。  [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] 專案特定的 WAP 子型別來建立 WAP 系統。 如需有關專案子類型的詳細資訊，請參閱 [專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
-   智慧型的網頁伺服器端的程式語言結合 HTML。 伺服器端語言稱為所包含的語言。 若要支援所包含的語言，必須實作的 Web 專案系統 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 系列的介面。  
  
    -   若要支援包含的語言在編輯器中，HTML 語言服務必須延後所包含的語言程式碼顯示包含的語言服務。  
  
    -   錯誤標記 （紅色曲線） 一定要建立程式碼編輯器的主要緩衝區中。  
  
## <a name="see-also"></a>請參閱  
 [Web 專案](../../extensibility/internals/web-projects.md)