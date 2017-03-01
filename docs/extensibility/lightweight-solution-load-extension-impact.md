---
title: "輕量型方案負載 (LSL) |Microsoft 文件"
ms.custom: 
ms.date: 01/17/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSPackages, lightweight solution load
- VSPackages, fast solution load
ms.assetid: 0a71d91e-dc71-4d6b-bbfe-9e4ecd9e5fd1
caps.latest.revision: 1
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
ms.sourcegitcommit: 221f4911981deec0330f76a82c0cc8a1b968e56e
ms.openlocfilehash: 28957abccc03001546038da10cf4ff7bbe21f63e
ms.lasthandoff: 02/22/2017

---
# <a name="lightweight-solution-load-lsl"></a>輕量型方案負載 (LSL)

## <a name="background-information-on-lsl"></a>LSL 的背景資訊

輕量型方案載入是 VS 2017 可大幅減少方案載入時間，讓您快速地在更有生產力的新功能。 啟用 LSL 時，Visual Studio 不會完全載入專案直到您開始使用它們。

LSL 可以影響 Visual Studio 擴充功能。 延伸模組的功能取決於要載入的專案不使用或無法正確運作，而不遵循本文中詳述的指引。

如需有關 LSL 進一步的背景，請使用下列連結︰

* [輕量型方案負載部落格](https://blogs.msdn.microsoft.com/visualstudio/2016/10/11/shorter-solution-load-time-in-visual-studio-15)
* 問題了嗎？ 與我們連絡[lslsupport@microsoft.com](mailto:lslsupport@microsoft.com)

## <a name="enable-the-setting-to-load-projects-in-deferred-mode"></a>啟用載入 「 延遲 」 模式中的專案設定

1. 關閉目前開啟的方案。
2. 移至**工具** > **選項** > **專案和方案** > **一般**設定 頁面。
3. 檢查**輕量型方案負載**方塊以啟用此設定。

以上述設定開啟開啟方案時，IDE 會顯示專案的一般檢視，但不是會載入專案。

## <a name="differences-between-deferred-load-and-regular-load-of-projects"></a>延後的載入和專案的一般負載之間的差異

輕量型方案負載，開啟方案時，不會載入專案。 這些 「 延後專案 」，會建立虛設常式階層。 [方案總管] 會顯示圖示和名稱的專案，以預期的檢視沒有 UI 指示 「 延後模式 」 中的部分或所有的專案。

使用啟用 LSL、 延伸模組不再可以預期時，就會觸發作業已經完全載入所需的專案。 呼叫端必須檢查它們是否具有相依性，在載入專案。 如果延伸模組需要延後的專案的資訊，請執行下列作業延伸模組︰

1. 視需要載入專案。
2. 使用新**工作區 Api**從延後的專案中取得資訊，而不載入它。

新**工作區 Api**允許從延後的專案取得的資訊，例如主控專案的原始程式檔和所有指定的專案的原始程式檔的副檔名。 在某些情況下，只有一組有限的專案需要載入。 正確的選項是作業的頻率、 方便的替代方法和整體使用者經驗之間取得平衡。

所有專案和方案負載相關 LSL 模式中，仍會引發事件。 這樣可讓元件以從 VS 取得預期的行為，而且它們的行為在相同的方式來載入專案的時間。 專案載入相關的工作完成時開啟的方案就可大幅減少不過。

## <a name="ui-requirements-and-changes"></a>UI 需求和變更

所有 UI 必須都將載入和延後的專案視為相等。 這表示可以在已載入的專案執行任何動作必須適用於延後的專案，但有些例外狀況。 為了完成這項作業的功能，有一些現有的平台 Api，以及引進的新 Api 的變更。

### <a name="expectations-for-ui"></a>UI 的期望

1. 功能必須顯示沒有視覺差異取決於是否專案正在載入或延後。
2. 任何清單或列舉型別載入專案的方案必須包含延後的專案。
3. 針對已載入專案可用的任何動作應該能根據延後的專案。
4. 功能必須要求載入專案時，才︰
  * 沒有直接的使用者互動的功能。 未事先載入專案。
  * 「 請參閱更結果 」 動作是使用者所做的。 請參閱以下這個 UI 指導方針。
  * 完全載入的專案可以用來滿足動作。 使用 LSL 和開啟專案 Api，可能的話，並傳送要求功能會要求功能時遺失。

### <a name="changes-in-platform-apis-to-help-drive-ui"></a>平台 Api 來驅動 UI 中的變更

1. 新的 Api，可用於要求方案已開啟輕量型方案負載模式和幾個專案都是延後的狀態。
2. 載入延後的所有專案方案中時，可供新的事件。
3. 新的 Api，可用於要求專案會延遲。
4. 現有的 Api 會更新為包含延後的專案，當要求已載入專案。
5. 更新現有的 Api，以快速解決之道是完全載入後開啟方案。

### <a name="how-to-add-see-more-results-for-a-feature"></a>如何加入 「 請參閱更結果 」 的功能。

專案的內容執行查詢的功能，應該考慮延後的專案的影響。 在某些情況下，功能可以向其查詢的結果 LSL 和工作區 Api 延後的專案。 在其他情況下，功能限制需要載入的專案。 這兩種情況應該提供新的 「 請參閱更結果 」 動作，可讓使用者完整載入專案和重新查詢。 此筆勢可讓您提供最佳近似值，同時讓使用者能夠實際載入專案時，取得完整結果延後的專案時的功能。

功能的一般演算法應該是︰

### <a name="when-the-query-is-performed-over-a-single-project"></a>當查詢是透過單一專案來執行

```csharp
// IsInDeferredState() and EnsureProjectIsLoadedHelper() in this sample can be found in the "Helpful code snippets" section of this document
public void Query(IVsHierarchy projectToQuery)
{
    // 1. Perform calculation/query
    DoQuery(projectToQuery);

    // 2. Present results to the user
    ShowResults();

    // 3. If the project was deferred, then present a "See More Results" UI element
    if (IsInDeferredState(projectToQuery))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Ask ask for the project to be loaded
    IVsHierarchy projectFromLastQuery = GetProjectFromLastQuery();
    IVsHierarchy loadedProject = EnsureProjectIsLoadedHelper(projectFromLastQuery);

    if (loadedProject != null)
    {
        // 2. Re-run the query on the loaded projects
        Query(loadedProject);
    }
    else
    {
        ShowErrorMessage();
    }
}
```

### <a name="when-the-query-is-performed-over-the-whole-solution"></a>當查詢是透過整個方案來執行

```csharp
// Requires Microsoft.VisualStudio.Shell.Interop.15.0.DesignTime.dll
public void Query()
{
    // 1. Perform calculation/query
    DoQuery();

    // 2. Present results to the user
    ShowResults();

    // 3. If there were deferred projects, then present a "See More Results from all projects" UI element
    var solution = // the solution
    object deferredCount = 0;
    int hr = ((IVsSolution)solution).GetProperty((int)__VSPROPID7.VSPROPID_DeferredProjectCount, out deferredCount);
    if (ErrorHandler.Succeeded(hr) && ((uint)deferredCount > 0))
    {
        ShowSeeMoreResults();
    }
}

public void OnClick_SeeMoreResults()
{
    // 1. Force the solution to load, as requested by the user. This brings up a UI with a "Cancel" button (unless supppresed with __VSBSLFLAGS.VSBSLFLAGS_NotCancelable)
    var solution = // get IVsSolution4
    int hr = ((IVsSolution4)solution).EnsureSolutionIsLoaded((uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    if (ErrorHandler.Succeeded(hr))
    {
        // 2. Re-run the query
        Query();
    }
    else
    {
        ShowErrorMessage();
    }
}
```

## <a name="api-changes"></a>API 變更

### <a name="new-api"></a>新的 API

IVsSolution7.IsSolutionLoadDeferred (out bool 延後)

如果目前方案已載入延後的模式，則傳回 true。 請注意，即使最後會延後的所有專案一開始方案載入延後的模式，如果載入目前的工作階段 （由於為明確的使用者動作或作業所強制），這個屬性仍會傳回 true。

__VSPROPID7。VSPROPID_DeferredProjectCount

傳回目前在延後的模式中的專案計數。 這個屬性都會在範圍 [0，VSPROPID_ProjectCount] 的值。

__VSHPROPID9。VSHPROPID_IsDeferred

如果專案階層架構中延後的載入狀態，則傳回 true。

值為 EPF_DEFERRED 和 EPF_NOTDEFERRED __VSENUMPROJFLAGS3

這些旗標可以傳遞至[IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx)來反覆查看延後和非延後的專案。

### <a name="new-events"></a>新的事件

IVsSolutionEvents7.OnAfterLoadAllDeferredProjects()

在載入延後的所有專案之後，會引發這個事件。 此時，VSPROPID_DeferredProjectCount 等於 0。 請注意，這個事件就不會引發方案負載的一部分，而且可能不會引發根本的工作階段中。 它只能被觸發時載入延後的所有專案。

### <a name="changes-to-existing-api"></a>變更現有的應用程式開發介面

* 傳遞[__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx)。若要 EPF_LOADEDINSOLUTION [IVsSolution.GetProjectEnum()](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.ivssolution.getprojectenum.aspx)傳回延後的專案。
* 傳遞[__VSENUMPROJFLAGS](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vsenumprojflags.aspx)。EPF_UNLOADEDINSOLUTION 不會傳回延後的專案。
* [KnownUIContexts.SolutionExistsAndFullyLoadedContext](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.knownuicontexts.solutionexistsandfullyloadedcontext.aspx)設為開啟的方案，則為 true。 延後的專案會被視為會載入此內容設定許多因此早於非 LSL 模式。
* [__VSPROPID](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.shell.interop.__vspropid.aspx)。VSPROPID_ProjectCount 傳回載入和延遲專案的總和。

## <a name="helpful-code-snippets"></a>很有幫助的程式碼片段

### <a name="check-if-a-solution-was-opened-in-deferred-load-mode"></a>檢查是否延後的負載模式所開啟的方案

```csharp
/// <summary>
/// Checks if the solution was opened in LSL mode.
/// </summary>
/// <returns>True if the solution was opened in LSL mode, false otherwise.</returns> public static bool IsSolutionLoadDeferred()
{
    IVsSolution7 vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution7;
    Assumes.Present(vsSolution);

    return vsSolution.IsSolutionLoadDeferred();
}
```

### <a name="check-if-a-project-is-deferred"></a>請檢查專案會延後

```csharp
/// <summary>
/// Checks to see if a project is deferred.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <returns>True if the project is deferred. False if it is any other state, such as loaded, unloaded, or virtual.</returns>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll</remarks>
public static bool IsInDeferredState(IVsHierarchy vsHierarchy)
{
    object deferred;
    int hr = vsHierarchy.GetProperty((int)VSConstants.VSITEMID.Root, (uint)__VSHPROPID9.VSHPROPID_IsDeferred, out deferred);

    if (ErrorHandler.Succeeded(hr))
    {
        return (bool)deferred;
    }

    return false;
}
```

### <a name="load-a-project"></a>載入專案

```csharp
/// <summary>
/// Ensures a project is fully loaded.
/// </summary> /// <param name="projectToLoad">A deferred or loaded project to ensure is loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IVsHierarchy EnsureProjectIsLoadedHelper(IVsHierarchy projectToLoad)
{
    int hr = VSConstants.S_OK;
    var solution = // get the solution

    // 1. Ask the solution to load the required project. To reduce wait time,
    //    we load only the project we need, not the entire solution.
    hr = projectToLoad.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid);
    hr = ErrorHandler.ThrowOnFailure(hr);
    hr = ((IVsSolution4)solution).EnsureProjectIsLoaded(projectGuid, (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 2. After the project is loaded, grab the latest IVsHierarchy object.
    IVsHierarchy loadedProject = null;
    hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
    hr = ErrorHandler.ThrowOnFailure(hr);

    return loadedProject;
}
```

### <a name="load-a-set-of-projects"></a>載入一組的專案

```csharp
/// <summary>
/// Ensures a collection of IVsHierarchys are loaded. To be used when deferred projects absolutely cannot be used.
/// </summary>
/// <param name="projectsToLoad">A set of deferred and/or loaded projects to ensure are loaded.</param>
/// <remarks>Requires Microsoft.VisualStudio.Shell.15.0.dll and Microsoft.VisualStudio.Shell.Interop.dll</remarks>
public static IReadOnlyCollection<IVsHierarchy> EnsureProjectsAreLoadedHelper(IReadOnlyCollection<IVsHierarchy> projectsToLoad)
{
    if (projectsToLoad == null || projectsToLoad.Count == 0)
        return projectsToLoad;

    int hr = VSConstants.S_OK;
    List<Guid> projectGuids = new List<Guid>(projectsToLoad.Count);
    List<IVsHierarchy> loadedProjects = new List<IVsHierarchy>(projectsToLoad.Count);
    var solution = // get the solution

    // 1. Collect projects to force load
    foreach (var project in projectsToLoad)
    {
        Guid projectGuid;
        hr = project.GetGuidProperty((uint)VSConstants.VSITEMID.Root, (int)__VSHPROPID.VSHPROPID_ProjectIDGuid, out projectGuid)
        hr = ErrorHandler.ThrowOnFailure(hr);
        projectGuids.Add(projectGuid);
    }

    // 2. Ask the solution to load the required projects. To reduce wait time,
    //    we load only the projects we need, not the entire solution.
    hr = ((IVsSolution4)solution).EnsureProjectsAreLoaded(projectCount, projectGuids.ToArray(), (uint)__VSBSLFLAGS.VSBSLFLAGS_None);
    hr = ErrorHandler.ThrowOnFailure(hr);

    // 3. After the projects are loaded, grab the latest IVsHierarchy objects
    foreach (var projectGuid in projectGuids)
    {
        IVsHierarchy loadedProject = null;
        hr = ((IVsSolution)solution).GetProjectOfGuid(projectGuid, out loadedProject);
        hr = ErrorHandler.ThrowOnFailure(hr);
        loadedProjects.Add(loadedProject);
    }

    return loadedProjects;
}
```

### <a name="checks-if-the-solution-has-deferred-projects"></a>會檢查方案已延後的專案

```csharp
/// <summary>
/// Checks if the solution has deferred projects
/// </summary>
/// <returns>True if the solution has deferred projects, false otherwise.</returns>
public static bool SolutionHasDeferredProjects()
{
    IVsSolution vsSolution = ServiceProvider.GlobalProvider.GetService(typeof(SVsSolution)) as IVsSolution;
    Assumes.Present(vsSolution);
    object varHasDeferredProjects;
    if (ErrorHandler.Succeeded(vsSolution.GetProperty(
        (int)__VSPROPID7.VSPROPID_DeferredProjectCount, out varHasDeferredProjects)))
    {
        return (int)varHasDeferredProjects != 0;
    }

    return false;
}
```

## <a name="getting-detailed-information-with-workspace-apis"></a>取得與工作區 Api 的詳細的資訊

### <a name="how-to-get-detailed-info-on-a-lsl-solution"></a>如何取得 LSL 解決方案的詳細的資訊

新的工作區 Api 會公開透過 IVsSolutionWorkspaceService 來擷取方案的詳細的資訊。

這些 Api 可以用來取得目前的工作區、 使用中的方案、 受管理的命令列資訊，以及工作區的 「 索引服務。 這些 Api 可以進一步利用索引服務以取得詳細的資料，所有原始程式檔在專案中，主控專案的原始程式檔的所有專案中目前的方案，包含所有專案等等的 P2P 參考。

下列程式碼片段會示範使用工作區 Api。

### <a name="get-ivssolutionworkspaceservice-initially"></a>一開始取得 IVsSolutionWorkspaceService

>**注意︰**請只在 LSL 情況下，以避免載入工作區 API 封裝取得 IVsSolutionWorkspaceService。

```csharp
private readonly Lazy<IVsSolutionWorkspaceService> _solutionWorkspaceService;

[ImportingConstructor]
public DeferredProjectWorkspaceService(SVsServiceProvider serviceProvider)
{
    _solutionWorkspaceService = new Lazy<IVsSolutionWorkspaceService>(
        () => (IVsSolutionWorkspaceService)serviceProvider.GetService(typeof(SVsSolutionWorkspaceService)));
}
```

>**注意︰**的下列程式碼片段假設已執行延遲初始化 _solutionWorkspaceService。

### <a name="get-managed-command-line-info-for-deferred-projects-for-active-solution-configuration"></a>取得受管理的命令列資訊延後的作用中方案組態的專案

```csharp
/// <summary>
/// Get the managed command line info for active solution configuration
/// </summary>
/// <param name="cancellationToken"> the cancellation token</param>
/// <returns></returns>
public async Task<IReadOnlyDictionary<string, ManagedCommandLineInfo>> GetManagedCommandLineInfoForConfigurationAsyn(CancellationToken cancellationToken)
{
    var dte = ServiceProvider.GetGlobalService(typeof(EnvDTE.DTE)) as EnvDTE.DTE;
    var solutionConfig = (EnvDTE80.SolutionConfiguration2)dte.Solution.SolutionBuild.ActiveConfiguration;

    // Solution configuration is something like "Debug|Any CPU"
    return await _solutionWorkspaceService.Value.GetManagedCommandLineInfoAsync(
        $"{solutionConfig.Name}|{solutionConfig.PlatformName}", cancellationToken).ConfigureAwait(false);
}
```

### <a name="get-the-active-solution-file-in-lsl"></a>取得使用中的方案中的檔案 LSL

```csharp
/// <summary>
/// Get the active solution file.
/// </summary>
/// <returns>The solution file.</returns>
public string GetActiveSolutionFile()
{
    return _solutionWorkspaceService.Value.SolutionFile;
}
```

### <a name="get-the-owning-project-of-a-source-file"></a>取得主控專案的原始程式檔

```csharp
/// <summary>
/// Get the owning projects of a source file.
/// </summary>
/// <param name="filePath">the source file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetOwningProjectAsync(string filePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var result = await indexService.GetFileDependantsAsync(filePath, null, String.Empty, (int)FileReferenceInfoType.Source);
    return result.Select(f => f.Path);
}
```

### <a name="get-all-source-files-from-a-project"></a>從專案取得所有原始程式檔

```csharp
/// <summary>
/// Get all source files from a project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, referenceTypes: (int)FileReferenceInfoType.Source);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-the-p2p-references-in-a-project"></a>在專案中取得 P2P 參考

```csharp
/// <summary>
/// Get outputs of project.
/// </summary>
/// <param name="projectFilePath">the project file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetFileReferenceAsync(string projectFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();
    var fileReferenceResult = await indexService.GetFileReferencesAsync(projectFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.Output);
    return fileReferenceResult.Select(f => f.Path);
}
```

### <a name="get-all-the-projects-in-a-solution"></a>取得方案中的所有專案

```csharp
/// <summary>
/// Get the projects in a solution.
/// </summary>
/// <param name="solutionFilePath">the solution file path.</param>
/// <returns></returns>
public async Task<IEnumerable<string>> GetProjectsInSolutionAsync(string solutionFilePath)
{
    var workspace = _solutionWorkspaceService.Value.CurrentWorkspace;
    var indexService = workspace.GetIndexWorkspaceService();

    // Passing the configuration|Platform that projects apply to; passing null will return projects with all configurations.
    var result = await indexService.GetFileReferencesAsync(solutionFilePath, context: "Debug|AnyCPU", referenceTypes: (int)FileReferenceInfoType.ProjectReference);
    return result.Select(f => f.Path);
}
```

## <a name="troubleshooting"></a>疑難排解

由於 LSL 本質，是刻意設計的使用者無法看到載入和延後的專案之間的差異。 這可讓功能開發和測試很困難。

您可以透過下列方式啟用延後的專案的使用者介面中的視覺提示︰

1. 關閉 Visual Studio
2. Regedit.exe
3. 選取 HKLM
4. 檔案 > 載入 Hive
5. `%localappdata%\microsoft\visualstudio\15.0_<instance ID>\privateregistry.bin`
6. 輸入 「 visual Studio 」 做為索引鍵名稱
7. 設定`HKLM\VisualStudio\Software\Microsoft\VisualStudio\15.0_<instanceID>\FeatureFlags\Solution\Loading\Deferred\Hint\Value=1`(DWORD)
8. 選取 HKLM\VisualStudio
9. 檔案 > 解除載入 Hive
10. 啟動 Visual Studio

如有任何進一步的問題，請將與[ lslsupport@microsoft.com ](mailto:lslsupport@microsoft.com)。







