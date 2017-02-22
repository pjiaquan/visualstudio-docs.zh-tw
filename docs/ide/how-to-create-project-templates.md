---
title: "如何：建立專案範本 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ExportTemplateWizard"
helpviewer_keywords: 
  - "專案範本, 建立"
  - "專案範本, 自訂範本位置"
  - "專案範本, 中繼資料檔"
  - "Visual Studio 範本, 建立專案範本"
  - "Visual Studio 範本, 專案範本"
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：建立專案範本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這個程序可以讓您使用 \[**匯出範本**\] 精靈建立封裝成 .zip 檔案的範本。  您也可以藉由使用匯出範本精靈副檔名，或使用包含在樣板建立的範本，以 VSIX 的檔案格式，針對改進部署[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]，或者您可以手動建立的範本。  
  
### 若要使用標準的匯出範本精靈建立自訂專案範本  
  
1.  建立專案。  
  
    > [!NOTE]
    >  針對將成為範本來源的專案進行命名時，請使用有效的識別項字元。  從名稱含有無效字元的專案所匯出的範本，可能會導致爾後以該範本為基礎的專案發生編譯錯誤。  如需有效識別項字元的詳細資訊，請參閱[Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)。  
  
2.  編輯專案，直到可以匯出做為範本為止。  
  
3.  請適當地編輯程式碼檔，以指示要執行參數取代的地方。  如需參數取代的詳細資訊，請參閱 [如何：替代樣板中的參數](../ide/how-to-substitute-parameters-in-a-template.md)。  
  
4.  按一下 \[**檔案**\] 功能表上的 \[**匯出範本**\]。  \[**匯出範本**\] 精靈隨即開啟。  
  
5.  按一下 \[**專案範本**\]。  
  
6.  如果目前的方案中有一個以上專案，請選取您要匯出至範本的專案。  
  
7.  按一下 \[**下一步**\]。  
  
8.  選取範本的圖示和預覽影像。  這些圖示和影像將出現在 \[**新增專案**\] 對話方塊中。  
  
9. 輸入範本名稱及相關的說明。  
  
10. 按一下 \[**完成**\]。  專案將匯出成 .zip 檔並放置在指定的輸出位置，另外如果有選取的話，將會匯入至 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
     如果已經安裝 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]，您可以使用 \[**VSIX 專案**\] 範本，將完成的範本包裝在 .vsix 檔案中以便進行部署。  如需詳細資訊，請參閱 [開始使用 VSIX 專案範本](../extensibility/getting-started-with-the-vsix-project-template.md)。  
  
## 請參閱  
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [如何：建立項目範本](../ide/how-to-create-item-templates.md)