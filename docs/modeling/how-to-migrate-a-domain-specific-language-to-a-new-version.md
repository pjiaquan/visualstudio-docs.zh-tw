---
title: "如何︰ 將定義域專屬語言移轉到新的版本 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a1ae073-443e-45ca-8bc9-9b944362b449
caps.latest.revision: 14
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: 3d07f82ea737449fee6dfa04a61e195654ba35fa
ms.openlocfilehash: 397efd1049ea52b2e7c67a46509d2a088c6fa488
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-migrate-a-domain-specific-language-to-a-new-version"></a>如何：將網域指定的語言移轉至新的版本
您可以移轉專案的定義和使用定義域專屬語言[!INCLUDE[vs2010](../misc/includes/vs2010_md.md)]版[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]，散發[!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)]。  
  
 移轉工具隨附的[!INCLUDE[vssdk_current_long](../misc/includes/vssdk_current_long_md.md)]。 工具會轉換[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案和方案使用，或定義 DSL 工具。  
  
 您必須明確執行移轉工具︰ 它無法自動啟動時開啟的方案中[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。 在這個路徑可以找到的工具和詳細的指引 > 文件︰  
  
 **%Program Files%\Microsoft Visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
## <a name="before-you-migrate-your-dsl-projects"></a>您之前移轉您的 DSL 專案  
 移轉工具會修改[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]專案檔 (**.csproj**) 和方案檔 (**.sln**)。  
  
#### <a name="to-prepare-projects-for-migration"></a>若要準備移轉專案。  
  
-   請確定**.csproj**和**.sln**可以寫入檔案。 如果原始檔控制下，確定已簽出。  
  
-   建立一份您想要移轉的資料夾。  
  
## <a name="migrating-a-collection-of-projects"></a>移轉專案的集合  
  
#### <a name="to-migrate-dsl-projects-and-solutions-to-visual-studio-2010"></a>若要移轉至 Visual Studio 2010 的 DSL 專案和方案  
  
1.  啟動 DSL 移轉工具。  
  
    -   您可以按兩下 Windows 檔案總管 （或檔案總管） 中的工具，或從命令提示字元啟動工具。 此工具會在這個位置︰  
  
         **%ProgramFiles%\Microsoft visual Studio 2010 SDK\VisualStudioIntegration\Tools\DSLTools\DslProjectsMigrationTool.exe**  
  
2.  選擇方案和您想要轉換的專案所在的資料夾。  
  
    -   在頂端的工具，方塊中輸入的路徑，或按一下**瀏覽**。  
  
     移轉工具會顯示樹狀結構的定義，或使用 Dsl 專案。 樹狀目錄包含使用每個專案**Microsoft.VisualStudio.Modeling.Sdk**或**TextTemplating**組件。  
  
3.  檢視樹狀目錄中的專案，並取消核取您不想要轉換的專案。  
  
    -   選取專案或方案，以查看此工具會進行的變更清單。  
  
        > [!NOTE]
        >  顯示資料夾名稱旁的核取方塊會有任何作用。 您必須展開要檢查專案和方案的資料夾。  
  
4.  轉換的專案。  
  
    1.  按一下 **轉換**。  
  
         每個專案檔轉換時，一份之前*專案***.csproj**會另存為*專案***。 vs2008.csproj**  
  
         每一份*方案***.sln**會另存為*方案***。 vs2008.sln**  
  
    2.  調查轉換所報告的任何失敗。  
  
         在文字視窗中，會回報失敗。 此外，樹狀檢視會顯示紅色旗標無法轉換每個節點上。 您可以按一下節點，以取得有關該失敗的詳細資訊。  
  
5.  **轉換所有範本**方案中包含順利轉換專案。  
  
    1.  開啟方案。  
  
    2.  按一下 [**轉換所有範本**方案總管] 中的標頭中的按鈕。  
  
        > [!NOTE]
        >  您可以進行此步驟中不必要的。 如需詳細資訊，請參閱[如何自動化轉換的所有範本](http://msdn.microsoft.com/en-us/b63cfe20-fe5e-47cc-9506-59b29bca768a)。  
  
6.  更新自訂程式碼中已轉換的專案。  
  
    -   嘗試建置專案，並調查任何失敗。  
  
    -   測試您的設計工具。  
  

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="see-also"></a>另請參閱  
 [相關部落格文章](https://blogs.msdn.microsoft.com/visualstudioalm/tag/code-index/)


