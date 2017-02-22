---
title: "Domain-Specific Language Tools 概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "網域指定的語言"
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 54
caps.handback.revision: 54
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Domain-Specific Language Tools 概觀
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

定義域專屬語言工具 \(DSL 工具\)，這些裝載於[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，可以讓您設計一種定義域專屬語言，然後產生所有項目，使用者必須能夠建立模型為基礎的語言。  
  
 DSL 工具包含下列工具：  
  
-   使用不同的方案範本\]，幫助您開始開發您的網域特定語言專案精靈。  
  
-   用於建立和編輯您的網域特定語言定義的圖形設計工具。  
  
-   驗證引擎，以確保定義域專屬語言定義正確，並顯示錯誤和警告，如果發生問題。  
  
-   程式碼產生器，以取得做為輸入的網域特定語言定義，並產生做為輸出的原始程式碼。  
  
## DSL 工具的解決方案  
 定義域專屬設計工具精靈會提供下列的方案範本：  
  
-   工作流程  
  
-   類別圖表  
  
-   最小的語言  
  
-   元件模型  
  
-   最小的 WPF  
  
-   最少的 Windows.Forms  
  
-   DSL 文件庫  
  
 如需詳細資訊，請參閱 [選擇網域指定的語言方案範本](../modeling/choosing-a-domain-specific-language-solution-template.md)。  
  
 精靈會建立[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]方案具有下列專案：  
  
-   Dsl  
  
     Dsl 專案定義網域特定語言和其編輯和處理工具。  
  
-   **DslPackage**  
  
     DslPackage 專案會決定如何與整合的語言工具[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## DSL 工具的圖形介面  
 您可以使用 DSL 工具的圖形介面，將項目和關聯性新增至您的網域特定語言。  新增項目之後，您可以將它們對應至圖案、 自訂色彩，以及新增裝飾來定義其外觀。  您也可以加入工具箱\] 中的項目。  
  
## 驗證在 DSL 工具  
 Dsl 會提供一個層級的驗證，請確定網域模型會符合用於產生程式碼的基本需求。  一般而言，當您建立您自己的定義域專屬語言時，即可將您自己的驗證，以表達您商務邏輯 」 規則。  如需有關自訂驗證的詳細資訊，請參閱[定義域專屬語言中的驗證](../modeling/validation-in-a-domain-specific-language.md)。  
  
 我們建議您先通常驗證定義域專屬語言在設計。  如果您的網域特定語言有驗證錯誤，無法產生原始程式碼。  從範本產生原始程式碼的過程藉由按一下**轉換所有的範本**在 \[方案總管\] 的工具列。  每當您修改語言定義，也請務必**轉換所有的範本**。  如需詳細資訊，請參閱 [如何：建立網域指定的語言方案](../modeling/how-to-create-a-domain-specific-language-solution.md)。  
  
## DSL 工具自訂作業  
 您可以提供額外的程式碼要調整模型的行為，以及透過您的語言定義的條件約束。  如有需要，您可以藉由修改文字範本中進行重大變更。  
  
## 發佈您的 DSL 方案  
 DSL 工具產生封裝裝載於[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  工具箱、 DSL 總管\] 中，與其他 UI 項目，可讓使用者藉由使用定義域專屬語言建立模型，則會顯示封裝。  
  
 當您建置並執行的 DSL 工具方案[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]，第二個實例[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]顯示您語言的使用者網域特定語言的外觀。請確認所有項目是否能正確運作之後，您可以散佈`.vsix` DslPackage 專案 \[組建\] 資料夾中，您會發現的檔案。  這個檔案可以用來安裝為 DSL [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]在其他電腦上的擴充功能。  如需詳細資訊，請參閱 [部署網域指定的語言方案](../modeling/deploying-domain-specific-language-solutions.md)。  
  
## 請參閱  
 [實驗執行個體](../extensibility/the-experimental-instance.md)   
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/zh-tw/ca5e84cb-a315-465c-be24-76aa3df276aa)