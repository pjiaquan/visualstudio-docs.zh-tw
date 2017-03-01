---
title: "方案 (。Sln) 檔案 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sln files, VSPackages
- solutions, .sln files
- .sln files, VSPackages
ms.assetid: 7d7ef539-2e4b-4637-b853-8ec7626609df
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d9b2d052f86cf76dcd9e2f97f2ee03eaf07dcf5b
ms.lasthandoff: 02/22/2017

---
# <a name="solution-sln-file"></a>方案 (。Sln) 檔案
解決方案是組織在 Visual Studio 專案的結構。 方案會維護文字為基礎 (共用） 的.sln 和.suo （二進位、 使用者專屬的解決方案選項） 檔案中的專案狀態資訊。 如需.suo 檔案的詳細資訊，請參閱[方案使用者選項 (。Suo) 檔案](../../extensibility/internals/solution-user-options-dot-suo-file.md)。  
  
 如果結果中的.sln 檔案參考載入 VSPackage 時，環境會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>.sln 檔案中讀取。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>  
  
 .Sln 檔案包含文字為基礎的環境使用尋找和載入保存的資料和它所參考的 Vspackage 專案的名稱 / 值參數資訊。 當使用者開啟方案時，環境會不斷循環`preSolution`， `Project`，和`postSolution`專案方案中的.sln 檔案載入方案中的資訊和任何永續性的資訊附加至方案。  
  
 每個專案檔包含由環境，以填入該專案的項目階層的其他資訊。 階層資料持續性是由專案; 控制資料不儲存中的.sln 檔案，雖然您可以特意專案將資訊寫入.sln 檔案如果您選擇這麼做。 與持續性的詳細資訊，請參閱[專案持續性](../../extensibility/internals/project-persistence.md)和[開啟和儲存專案項目](../../extensibility/internals/opening-and-saving-project-items.md)。  
  
## <a name="solution-file-contents"></a>方案檔案內容  
 .Sln 檔案包含數個區段，如下列程式碼所示。  
  
```  
Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1", "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
EndProject  
Global  
  GlobalSection(SolutionNotes) = postSolution  
  EndGlobalSection  
  GlobalSection(SolutionConfiguration) = preSolution  
       ConfigName.0 = Debug  
       ConfigName.1 = Release  
  EndGlobalSection  
  GlobalSection(ProjectDependencies) = postSolution  
  EndGlobalSection  
  GlobalSection(ProjectConfiguration) = postSolution  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.ActiveCfg = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Debug.Build.0 = Debug|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.ActiveCfg = Release|x86  
   {8CDD8387-B905-44A8-B5D5-07BB50E05BEA}.Release.Build.0 = Release|x86  
  EndGlobalSection  
  GlobalSection(ExtensibilityGlobals) = postSolution  
  EndGlobalSection  
  GlobalSection(ExtensibilityAddIns) = postSolution  
  EndGlobalSection  
EndGlobal  
```  
  
 若要載入的方案，環境會執行下列工作順序。  
  
1.  環境讀取.sln 檔案的全域區段，並處理標記的所有區段`preSolution`。 在此情況下，還有一個這類陳述式︰  
  
    ```  
    GlobalSection(SolutionConfiguration) = preSolution  
         ConfigName.0 = Debug  
         ConfigName.1 = Release  
    ```  
  
     當環境讀取`GlobalSection('name')`標記，它會將名稱對應到 VSPackage 使用登錄。 索引鍵的名稱必須存在於登錄 [HKLM\\<Application id="" registry=""></Application>\>\SolutionPersistence\AggregateGUIDs]。 機碼中的預設值為 VSPackage 所撰寫的項目封裝的 GUID (REG_SZ)。  
  
2.  在環境載入 VSPackage，呼叫`QueryInterface`上的 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>介面，並呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A>方法中的區段，VSPackage 才能儲存資料的資料。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.ReadSolutionProps%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps> 環境會針對每個重複此程序`preSolution`一節。  
  
3.  環境逐一查看專案持續性區塊。 在此情況下，是一個專案。  
  
    ```  
    Project("{F184B08F-C81C-45F6-A57F-5ABD9991F28F}") = "Project1",  
    "Project1.vbproj", "{8CDD8387-B905-44A8-B5D5-07BB50E05BEA}"  
    EndProject  
    ```  
  
     此陳述式包含唯一的 GUID 專案和專案類型的 GUID。 環境會用這項資訊來尋找屬於方案的專案檔案並 VSPackage 所需的每個專案。 GUID 會傳遞至專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>載入特定的專案相關的 VSPackage，然後專案由載入 VSPackage。</xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory> 在此情況下，此專案載入 VSPackage 為 Visual Basic。  
  
     每個專案可將唯一的專案執行個體識別碼，使它可以視需要進行其他方案中的專案存取。 在理想情況下，如果方案和專案原始程式碼控制之下，專案的路徑應該相對於方案的路徑。 當第一次載入方案時，專案檔不能在使用者機器上。 沒有專案檔案儲存在相對於方案檔案伺服器上，是相當簡單的專案檔，以找到並複製到使用者的電腦。 然後複製並載入其餘的專案所需的檔案。  
  
4.  根據專案 > 一節中的.sln 檔案中包含的資訊，則環境會載入每個專案檔。 專案本身還負責填入專案階層架構和載入任何巢狀的專案。  
  
5.  處理的.sln 檔案的所有區段之後，解決方案會顯示在 [方案總管] 中，並可供使用者修改。  
  
 如果無法載入，任何實作專案方案中的 VSPackage<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A>方法呼叫和方案中的每個專案會有機會來略過它可能會在載入期間所做的變更。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.OnProjectLoadFailure%2A> 如果剖析錯誤發生，請保留資訊越多越好的方案檔案和環境會顯示一個對話方塊，警告使用者方案已損毀。  
  
 儲存或關閉，此方案時<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A>方法呼叫並傳遞至該階層，查看是否已變更的方案需要輸入.sln 檔案。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.QuerySaveSolutionProps%2A> Null 值，傳遞至`QuerySaveSolutionProps`中<xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS>，表示方案保存資訊。</xref:Microsoft.VisualStudio.Shell.Interop.VSQUERYSAVESLNPROPS> 如果值不是 null，保存的資訊是針對特定的專案，取決於指標<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>介面。</xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
 如果要儲存資訊<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence>介面的指標呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A>方法。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.SaveSolutionProps%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>然後會呼叫方法來擷取名稱 / 值組，從環境`IPropertyBag`介面，並將資訊寫入至的.sln 檔案。</xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps.WriteSolutionProps%2A>  
  
 `SaveSolutionProps`和`WriteSolutionProps`物件會以遞迴方式呼叫擷取資訊以從儲存環境`IPropertyBag`介面之前所有的變更已輸入的.sln 檔案。 如此一來，您可以確保解決方案與可用下次開啟解決方案時，將會保存資訊。  
  
 每個載入的 VSPackage 都會列舉出來，看看是否有任何項目儲存至.sln 檔案。 它是只在會查詢登錄機碼的載入時間。 因為它們是在記憶體中儲存的解決方案時，環境會知道有關的所有載入的封裝。  
  
 .Sln 檔案包含中的項目僅`preSolution`和`postSolution`區段。 因為解決方案需要這項資訊來正確載入.suo 檔案中沒有類似的區段。 .Suo 檔案包含使用者特定的選項，例如私人筆記，不能共用或放置在原始程式碼控制之下。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps></xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionProps>   
 [方案使用者選項 (。Suo) 檔案](../../extensibility/internals/solution-user-options-dot-suo-file.md)   
 [解決方案](../../extensibility/internals/solutions.md)
