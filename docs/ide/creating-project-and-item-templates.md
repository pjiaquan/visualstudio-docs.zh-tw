---
title: "在 Visual Studio 中建立自訂專案與項目範本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "項目範本, 關於項目範本"
  - "專案範本 [Visual Studio], 關於專案範本"
  - "範本 [Visual Studio], 關於樣板"
  - "範本 [Visual Studio], 項目"
  - "範本 [Visual Studio], 專案"
  - "Visual Studio 範本, 關於樣板"
  - "Visual Studio 範本, 項目"
  - "Visual Studio 範本, 專案"
ms.assetid: a6ce501a-699b-4e3e-ade8-c81895645c20
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 在 Visual Studio 中建立自訂專案與項目範本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案範本和項目範本提供可重複使用的 Stub，讓使用者有一些基本的程式碼和結構可自行運用。  
  
## Visual Studio 範本  
 安裝 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 時會安裝一些預先定義的專案範本和項目範本。  \[**新增專案**\] 對話方塊中可用的 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 和 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] Windows Form 應用程式和類別庫，就是專案範本的例子。  已安裝的項目範本位於 \[**加入新項目**\] 對話方塊中，包括程式碼檔案、XML 檔案、HTML 網頁和樣式表等項目。  
  
 使用者可將這些範本當做起點，開始建立專案或擴充目前專案。  專案範本提供特定專案類型所需的檔案、包含標準組件參考，並設定預設專案屬性和編譯器選項。  項目範本可能只是一個有正確副檔名的空檔案，也可能是一個多檔案項目那麼複雜，例如，項目中包含原始程式碼檔案 \(含有 Stub 程式碼\)、設計工具資訊檔案和內嵌資源。  
  
 除了 \[**新增專案**\] 和 \[**加入新項目**\] 對話方塊中已安裝的範本，您也可以撰寫自己的範本，或下載並使用由社群建立的範本。  如需詳細資訊，請參閱[如何：建立專案範本](../ide/how-to-create-project-templates.md)和[如何：建立項目範本](../ide/how-to-create-item-templates.md)。  
  
## 範本的內容  
 所有專案範本和項目範本，不論是隨 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 一起安裝或由您建立，都以相同的原理運作且具有相似的內容。  所有範本都包含下列項目：  
  
-   使用範本時要建立的檔案。  這包括原始程式碼檔案、內嵌資源、專案檔等等。  
  
-   一個 .vstemplate 檔案。  此檔案包含的中繼資料提供必要資訊，讓 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 在 \[**新增專案**\] 和 \[**加入新項目**\] 對話方塊中顯示範本，以及從範本建立專案或項目。  如需 .vstemplate 檔案的詳細資訊，請參閱[樣板參數](../ide/template-parameters.md)。  
  
 當這些檔案壓縮成 .zip 檔案並放入正確的資料夾時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會自動顯示它們。  專案範本出現在 \[**新增專案**\] 對話方塊的 \[**我的範本**\] 區段中，而項目範本出現在 \[**加入新項目**\] 對話方塊中。  如需範本資料夾的詳細資訊，請參閱[如何：尋找並整理範本](../ide/how-to-locate-and-organize-project-and-item-templates.md)。  
  
## 入門套件  
 入門套件是增強的範本，可以與社群的其他成員共用。  入門套件包含可編譯的程式碼範例、文件和其他資源，協助使用者經由建置實際有用的應用程式，學習新的工具和程式設計技巧。  入門套件的基本內容和程序，與範本完全相同。  如需詳細資訊，請參閱[如何：建立入門套件](../ide/how-to-create-starter-kits.md)。  
  
## 請參閱  
 [如何：建立專案範本](../ide/how-to-create-project-templates.md)   
 [如何：建立項目範本](../ide/how-to-create-item-templates.md)   
 [樣板參數](../ide/template-parameters.md)   
 [自訂範本](../ide/customizing-project-and-item-templates.md)   
 [如何：建立入門套件](../ide/how-to-create-starter-kits.md)