---
title: "建立方案和專案 | Microsoft Docs"
ms.custom: 
ms.date: 03/21/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.openprojectfromweb
- vs.newproject
- VS.ToolsOptionsPages.Projects.General
- SolutionItemsProject
helpviewer_keywords:
- solutions [Visual Studio], deleting
- solutions [Visual Studio], creating
- projects [Visual Studio], creating
ms.assetid: 836f8ca0-3fc9-4f4b-9090-45f2e4d2e9c8
caps.latest.revision: 46
author: kempb
ms.author: kempb
manager: ghogen
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 9a4b04dc59c409a5c68ad1fb376abb33b3859ff6
ms.contentlocale: zh-tw
ms.lasthandoff: 05/24/2017

---

# 建立方案和專案
<a id="create-solutions-and-projects" class="xliff"></a>

專案是邏輯容器，以儲存建置您應用程式所需的所有檔案。 選擇主要功能表中的 [檔案]、[新增]、[專案] 來建立專案時，[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 會建立一個包含該專案的方案。 您接著可以視需要將更多新的或現有專案加入方案。 您可以從現有的程式碼檔案建立專案，而且您可以建立暫存專案 (僅限 .NET)，當專案完成後，將刪除暫存專案。

> [!NOTE]
>  本主題中的描述以 Visual Studio Community 版本為基礎。 您看到的對話方塊與功能表命令，可能會依您的設定與 Visual Studio 版本而與此處描述的有所不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱[將 Visual Studio IDE 個人化](../ide/personalizing-the-visual-studio-ide.md)。

## 從已安裝的專案範本建立專案
<a id="create-a-project-from-an-installed-project-template" class="xliff"></a>  
 在主要功能表上，選擇 [檔案]、[新增]、[專案]，以顯示 [新增專案] 對話方塊。 在 [已安裝]、[範本] 下的左窗格中，選擇程式設計語言與平台或技術，然後從中間窗格的可用範本中進行選擇。  

 在 [新增專案]  對話方塊中，[方案]  下拉式清單可讓您選擇在新的或現有方案中建立新專案，或在新的 Visual Studio 執行個體中建立新專案。  

## 從現有程式碼檔案建立專案
<a id="create-a-project-from-existing-code-files" class="xliff"></a>  
 如果您有鬆散來源檔案的集合，則可以輕鬆地建立包含這些檔案的專案。 選擇 [檔案]、[新增]、[現有程式碼中的專案] 啟動 [從現有程式碼檔建立專案精靈]，然後遵循提示。  

> [!TIP]
>  這個選項最適合用於比較簡單的檔案集合。  

## 建立暫存的專案 (C# 和 Visual Basic)
<a id="create-a-temporary-project-c-and-visual-basic" class="xliff"></a>
 藉由使用暫存專案，您可以建立和試驗 .NET 專案，而不必指定磁碟位置。 建立專案時，只需要選取專案類型和範本，並在 [新增專案]  對話方塊中指定名稱。 使用暫存專案時，隨時都可以儲存或捨棄它。  

## 建立以特定 .NET Framework 版本為目標的 .NET 專案
<a id="create-a-net-project-that-targets-a-specific-version-of-the-net-framework" class="xliff"></a>  
 您可以使用 [新增專案]  對話方塊上方的 [.NET Framework]  版本下拉式功能表，針對較早版本的 .NET Framework 建立專案。 因為只有與該 .NET Framework 版本相容的範本才會出現在清單中，所以請在選取專案範本之前設定此值。  

 您必須在系統上安裝 .NET Framework 3.5，才能存取早於 4.0 的 Framework 版本。  

## 下載範例方案
<a id="download-sample-solutions" class="xliff"></a>  
 您可以使用 Visual Studio 從 [MSDN Code Gallery](http://go.microsoft.com/fwlink/?LinkId=254185) 及其他來源 (例如 Git 存放庫) 下載並安裝範例方案。

 您可以分別下載範例，也可以下載範例套件，其中包含共用技術或主題的相關範例。 如果您下載的任何範例有原始程式碼變更發行，您就會收到通知。  

 如需詳細資訊，請參閱 [Visual Studio 範例](../ide/visual-studio-samples.md)。  

## 在方案層級新增單一檔案
<a id="add-single-files-at-the-solution-level" class="xliff"></a>  
 有時候您的檔案可能會有多個專案參考它，或是包含邏輯上屬於方案層級的文字或其他資料，而不是在特定專案下。  將單一項目新增至方案︰  

- 在方案總管中以滑鼠右鍵按一下方案節點，然後選擇 [新增]、[新增項目] 或 [新增]、[現有項目]。  

## 建立空的方案
<a id="create-empty-solutions" class="xliff"></a>  
 雖然專案可以位於方案中，但是您也可以建立沒有專案的方案。 您也可以開啟程式碼專案，而不需要方案。

#### 建立空的方案
<a id="to-create-an-empty-solution" class="xliff"></a>  

1.  在 [檔案] 功能表上，依序選擇 [新增]、[新增專案]。  

2.  在左窗格中，依序選擇 [已安裝]、[其他專案類型]，然後從展開的清單中選擇 [Visual Studio 方案]。  

3.  在中間窗格選擇 [空白方案]。  

4.  為您的方案設定 [名稱] 及 [位置] 值，然後選擇 [確定]。  

建立空的方案之後，您可以在 [專案] 功能表上，選擇 [新增項目] 或 [新增現有項目]，將新專案或項目或是現有專案或項目新增至該方案。

### 刪除方案
<a id="delete-solutions" class="xliff"></a>  
 您可以永久刪除方案，但不是使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 來刪除。 刪除方案之前，請移動您可能再次用於另一個方案的任何專案。 然後使用 [檔案總管] 來刪除包含 .sln 和 .suo 方案檔案的目錄。  

> [!NOTE]
>  .Suo 檔案是隱藏檔案，不會顯示在預設的 [檔案總管] 設定下。  

##### 刪除方案
<a id="to-delete-a-solution" class="xliff"></a>  

1.  在方案總管中，於您要刪除之方案的方案總管操作 (右鍵) 功能表上，選擇 [在檔案總管中開啟資料夾]。

2.  在 [檔案總管] 中，瀏覽上一層。

3.  選擇包含方案的目錄，然後按 DELETE 鍵。

## 另請參閱
<a id="see-also" class="xliff"></a>  
 [專案和方案](../ide/solutions-and-projects-in-visual-studio.md)   

