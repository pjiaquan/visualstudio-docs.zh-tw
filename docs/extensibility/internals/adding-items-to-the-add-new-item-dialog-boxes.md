---
title: "加入項目來加入新項目對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "加入新項目] 對話方塊，加入項目"
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 加入項目來加入新項目對話方塊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

將項目加入的程序 **加入新項目** 對話方塊開頭的登錄機碼。 下列的登錄項目所示，AddItemTemplates 區段包含的路徑和名稱的目錄中的項目可在 \[ **加入新項目** 放\] 對話方塊。  
  
> [!NOTE]
>  表格後面的程式碼片段包含其他資訊的登錄項目。  
  
 \[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\14.0Exp\\Projects\] 即可找到這一節。  
  
 第一個 GUID 是這種; 專案的 CLSID第二個 GUID 表示新增的項目範本的已註冊的專案類型。  
  
 \\{C061DB26\-5833\-11D2\-96F5\-000000000000}\\AddItemTemplates\\TemplateDirs\\ {ACEF4EB2\-57CF\-11D2\-96F4\-000000000000} \\1  
  
 @\="\#6"  
  
 "TemplatesDir"\="\< Visual Studio SDK 安裝 path\\\\VSIntegration\\\\SomeFolder\\\\SomePackage\\\\SomeProject\\\\SomeProjectItems 」  
  
 「 SortPriority 」 \= dword:00000064  
  
|名稱|類型|\(.Rgs 檔案資料\)|描述|  
|--------|--------|-------------------|--------|  
|@ \(預設值\)|REG\_SZ|\#%IDS\_ADDITEM\_TEMPLATES\_ENTRY %|資源識別碼 **加入項目** 範本。|  
|Val TemplatesDir|REG\_SZ|%TEMPLATE\_PATH%\\SomeProjectItems|顯示的對話方塊中的專案項目路徑 **加入新項目** 精靈。|  
|Val SortPriority|REG\_DWORD|100 \([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]\)|樹狀節點中顯示的檔案中的排序順序會決定 **加入新項目** 對話方塊。|  
  
> [!NOTE]
>  Visual C\# 和 Visual Basic 專案類型的 GUID 如下:[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0\-301F\-11D3\-BF4B\-00C04F79EFBC}[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F\-C81C\-45F6\-A57F\-5ABD9991F28F}  
  
 目錄所列的節點上的左半部 TemplateDirs，也就是 %template\_path%\\someprojectitems，為 **加入新項目** 對話方塊方塊樹狀結構。 在樹狀目錄中的其他項目為基礎的子目錄的根目錄中。 可加入至專案的檔案是在右窗格中的項目 **加入新項目** 對話方塊。  
  
 一般而言，這個資料夾會包含 HTML 範本或.cpp 檔案中，例如您專案的範本檔案和任何.vsz 檔案來啟動精靈。 若要控制的項目顯示的方式，您也可以包含.vsdir 檔案將當地語系化的目錄名稱和圖示。 當地語系化的字串會出現在對話方塊中，表示此節點在樹狀目錄中加入新項目\] 對話方塊的標題。  
  
 不過，您不需要的所有項目有一個.vsdir 檔案中。 您可以有一個.vsdir 檔案的目錄中的每個項目。 如需詳細資訊，請參閱[精靈 \(。Vsz\) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)與[範本目錄描述 \(。Vsdir\) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)。  
  
> [!NOTE]
>  .Vsdir 檔案範本目錄中的是選擇性的。 如果您只想要放置在目錄中的專案項目，並顯示在 **加入新項目** 對話方塊中，您可以將該檔案置 TemplatesDir 陳述式中指定的範本目錄中。 檔案就會顯示在右窗格中 **加入新項目** 該專案的對話方塊。 不過，如果您想要顯示當地語系化的標題，檔案或圖示，您必須包含至少一個.vsdir 檔案範本目錄中。  
  
## 群組專案項目  
 如果您想要包含範本資料夾中的群組 **加入新項目** 對話方塊方塊樹狀目錄中，您必須使用的項目範本根目錄底下的子目錄中。 當 **加入新項目** 對話方塊顯示給使用者，他們也會看到子資料夾，並能從中選取專案項目。  
  
 在程式碼區段之排序優先順序會決定相對於其他項目樹狀結構節點的樹狀目錄中建立此範本目錄的位置。 如 **加入新項目** \] 對話方塊之排序優先順序是所有您必須包含您的項目將會顯示在對話方塊中的正確位置。  
  
 您也可以實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> 介面，以篩選顯示之內容 **加入新項目** 對話方塊。 藉由實作這個介面，您可以設定一個範本目錄，例如，包含的磁碟上 50 的範本和精靈檔案。 如此一來，您可以使用隸屬於一個專案類型、 其他 30 檔案屬於另一個專案類型和一般類型的專案中可用的所有檔案的 20 個檔案的不同專案類型。 在這種方式，根據哪個專案建立範本，您可以顯示一組不同的範本檔案。  
  
 例如，在 Visual Basic 專案中，您可能必須 Web 專案和用戶端專案。 Web form 有用的項目加入至用戶端專案，而且非 windows form 不是有用的項目加入至 Web 伺服器專案。 因此，您可以建立一個包含這兩種專案類型的所有檔案的範本目錄。 然後藉由實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, ，您可以隱藏的項目不會顯示根據專案或專案中的專案設定的類型。  
  
## 篩選的專案項目  
 `IVsFilterAddProjectItemDlg2` 提供下列方式篩選樹狀目錄 \(左窗格\) 和專案檔 \(右窗格\) 中的項目:  
  
-   所提供的當地語系化名稱 \(.vsdir 檔案中所含的對話方塊中顯示的標題\) `IVsFilterAddProjectItemDlg`。  
  
-   由檔案和資料夾在磁碟上的實際名稱 \(非當地語系化 — 沒有.vsdir 檔案\) 所提供 `IVsFilterAddProjectItemDlg`。  
  
-   依類別、 提供 `IVsFilterAddProjectItemDlg2`。  
  
 若要依類別篩選，請提供.vsdir 檔案，例如 「 Web 表單 」 中的項目或在 Visual Basic 中的 「 用戶端項目 」 的類別目錄字串。 然後對話方塊程式碼從.vsdir 檔案擷取分類分類，並將它傳遞給您。 接著可以將該資訊傳遞至您的實作 `IVsFilterAddProjectItemDlg2` 篩選 **加入新項目** \] 對話方塊中，依照分類。 針對網頁或用戶端 Win32 應用程式的情況下，您也可以篩選項目。 此外，您可以識別 [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 標記項目做為 Microsoft Foundation Classes \(MFC\) 或使用中的範本程式庫 \(ATL\) 項目。 當您找出這些項目時，專案系統可以定義自己的分類，以便系統可以根據類別和分類篩選。  
  
 如果您實作此篩選器 」 功能，您沒有對應的資料表應該隱藏每個項目。 只要將項目分類為型別，並放在.vsdir 檔案或檔案的分類。 然後您可以隱藏任何實作介面有特定分類的項目。 如此一來，您可以進行中的項目 **加入新項目** 對話方塊方塊動態根據專案中的狀態。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [物件，通常會用來擴充專案的 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [範本目錄描述 \(。Vsdir\) 檔案](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [精靈 \(。Vsz\) 檔案](../../extensibility/internals/wizard-dot-vsz-file.md)