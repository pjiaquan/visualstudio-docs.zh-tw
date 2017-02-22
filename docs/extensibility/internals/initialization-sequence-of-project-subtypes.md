---
title: "專案子類型的初始化順序 | Microsoft Docs"
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
  - "專案的子類型，初始化順序"
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 專案子類型的初始化順序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

環境呼叫的基底專案工廠實作來建構專案<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>。  專案檔案的副檔名的專案類型的 GUID 清單不是空的環境決定時，就會啟動專案的子型別建構。  將專案檔案的副檔名\] 和 \[GUID 的專案指定專案是否[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]或[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案類型。  比方說，.vbproj 副檔名，並找出 {F184B08F\-C81C\-45F6\-A57F\-5ABD9991F28F} [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]專案。  
  
## 專案子類型的環境的初始設定  
 下列程序詳細說明專案系統，由多個專案的子型別彙總初始設定順序。  
  
1.  環境呼叫基底專案的<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>，專案會剖析它的專案檔時發現不是彙總的專案類型的 Guid 清單，並`null`。  專案會停止直接建立它的專案。  
  
2.  專案呼叫`QueryService`的<xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject>服務，來建立專案子類型使用的環境的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>方法。  這個方法內的環境可讓您實作的遞迴函式呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>， `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)`和<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>方法，而它查核專案的清單型別開始的最外層的專案子類型的 Guid。  
  
     以下將詳細說明的初始化步驟。  
  
    1.  環境的實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>方法呼叫`HrCreateInnerProj```包含下列的函式宣告的方法：  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         這個函式呼叫時第一次，也就是對最外層的專案子型別參數`pOuter`和`pOwner`做為傳入的`null`函式會設定最外層的專案子類型與`IUnknown`到`pOuter`。  
  
    2.  接下來環境呼叫`HrCreateInnerProj`與第二個專案中的型別 GUID 清單的函式。  這個 GUID 對應至基底的專案中，彙總的序列向逐步執行的第二個內嵌專案子類型。  
  
    3.  `pOuter`現在指向`IUnknown`的最外層的專案子型別，和`HrCreateInnerProj`的實作會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>後面的實作呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>。  在<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>控制您所傳遞的方法`IUnknown`的最外層的專案子類型中， `pOuter`。  擁有的專案 \(內嵌專案子類型\)，就必須建立它的彙總的專案物件。  在<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>您傳入的指標的方法實作`IUnknown`的彙總內部的專案。  這兩種方法建立彙總物件，而且您的實作需要遵守 COM 彙總規則，以確保專案子類型沒有結束最多保留對其本身的參考次數。  
  
    4.  `HrCreateInnerProj`您的實作會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>。  這種方法的專案子類型進行初始設定工作。  您可以，比方說，註冊方案中的事件<xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>。  
  
    5.  `HrCreateInnerProj`會呼叫以遞迴方式，直到到達最後一個 GUID \(基底的專案\)，在清單中。  針對每一個這些呼叫，請重複步驟 c 到 d。  `pOuter`指到最外層的專案子類型`IUnknown`每個層級的彙總。  
  
 下列範例詳述大約表示中以程式設計方式的程序<xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A>環境由存取關聯式資料庫為它的方法。  程式碼只是一個範例。 它並不適合進行編譯，並使文字更明確移除了所有的錯誤檢查。  
  
## 範例  
  
### 程式碼  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [專案子類型](../../extensibility/internals/project-subtypes.md)