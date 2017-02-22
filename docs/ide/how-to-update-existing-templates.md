---
title: "如何：更新現有的範本 | Microsoft Docs"
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
  - "項目範本, 更新現有的範本"
  - "專案範本, 更新現有的範本"
  - "Visual Studio 範本, 更新現有的範本"
ms.assetid: d585e45b-7fe2-45fa-9cf3-7f2bc060f3c4
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 如何：更新現有的範本
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在建立範本並將檔案壓縮成 .zip 檔之後，您可能想要修改範本。  若要執行此動作，您可以手動變更範本中的檔案，或從以範本為基礎的專案中匯出新範本。  
  
## 使用匯出範本精靈更新現有範本  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 提供可用來更新現有範本的 \[**匯出範本**\] 精靈。  
  
#### 使用匯出範本更新現有範本  
  
1.  在 \[檔案\] 功能表上，按一下 \[新增\] 及 \[新增專案\]。  
  
2.  選取您想要更新的範本，輸入暫存專案的名稱和位置，然後按一下 \[**確定**\]。  
  
3.  在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 中修改專案。  
  
4.  在 \[**檔案**\] 功能表上按一下 \[**匯出範本**\]，並使用 \[**匯出範本**\] 精靈建立新的範本。  
  
5.  更新的範本壓縮成 .zip 檔之後，請刪除舊範本的 .zip 檔。  
  
## 手動更新現有範本  
 您可以藉由修改壓縮 .zip 檔中的檔案，在 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 以外更新現有範本。  
  
#### 手動更新現有範本  
  
1.  找出包含樣板的.zip 檔。  根據預設，此檔案位於 \\My Documents\\Visual Studio *Version*\\My Exported Templates\\ 中。  
  
2.  將 zip 檔解壓縮。  
  
3.  修改或刪除目前的範本檔，或將新檔案加入至範本。  
  
4.  開啟、修改和儲存.vstemplate XML 檔，以處理更新的行為或新檔案。  如需 .vstemplate 結構描述的詳細資訊，請參閱 Visual [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)。  如需關於您可以在來源檔案中參數化哪些項目的詳細資訊，請參閱[範本參數](../ide/template-parameters.md)。  
  
5.  在範本中選取檔案，按一下滑鼠右鍵，按一下 \[**傳送到**\]，然後按一下 \[**壓縮的 \(zipped\) 資料夾**\]。  您選取的檔案即會壓縮成 .zip 檔。  
  
6.  將新的 .zip 檔放在與舊 .zip 檔相同的目錄中。  
  
7.  刪除已解壓縮的樣板檔案和舊樣板 .zip 檔案。  
  
8.  啟動 \(以系統管理員身分\) 開發人員命令提示字元的執行個體 \(位於 \[開始\] 功能表上的 **Visual Studio 2010 \/ Visual Studio Tools\/Developer Command Prompt** 下\)。  
  
9. 執行下列命令：`devenv /installvstemplates`  
  
## 請參閱  
 [自訂範本](../ide/customizing-project-and-item-templates.md)   
 [建立自訂專案與項目範本](../ide/creating-project-and-item-templates.md)   
 [Visual Studio 範本結構描述參考](../extensibility/visual-studio-template-schema-reference.md)   
 [範本參數](../ide/template-parameters.md)   
 [如何：建立入門套件](../ide/how-to-create-starter-kits.md)