---
title: "公開專案物件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "公開的專案物件"
  - "擴充性專案物件"
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# 公開專案物件
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

自訂專案類型可以提供 automation 物件，以便允許存取使用自動化介面的專案。 每個專案類型需要提供標準 <xref:EnvDTE.Project> 從存取的 automation 物件 <xref:EnvDTE.Solution>, ，其中包含在 IDE 中開啟的所有專案的集合。 在專案中的每個項目所要公開 <xref:EnvDTE.ProjectItem> 物件存取具有 <xref:Project.ProjectItems>。 除了這些標準 automation 物件，可以選擇提供特定專案的 automation 物件的專案。  
  
 您可以建立自訂的根層級自動化物件，您可以存取晚期繫結從根 DTE 物件使用 `DTE.<customeObjectName>` 或 `DTE.GetObject(“<customObjectName>”)`。 例如，Visual c \+ \+ 建立名為 「 VCProjects 」，您可以使用 DTE 存取 c \+ \+ 專案特定的專案集合。VCProjects 或 DTE。GetObject\("VCProjects"\)。 您也可以建立 Project.Object，這是唯一的專案類型中 Project.CodeModel，您可以查詢其最具衍生性的物件，而專案項目，會公開 ProjectItem.Object 和 ProjectItem.FileCodeModel。  
  
 它是公開為自訂的特定專案的專案集合的專案的常見慣例。 例如， [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] 建立 c \+ \+ 特定的專案集合，然後，您可以存取使用 `DTE.VCProjects` 或 `DTE.GetObject("VCProjects")`。 您也可以建立 `Project.Object`, ，這是唯一的專案類型中 `Project.CodeModel`, ，其最具衍生性的物件，其中您可以查詢 `ProjectItem`, ，以公開 `ProjectItem.Object`, ，和 `ProjectItem.FileCodeModel`。  
  
### 參與專案的 VSPackage 特定物件  
  
1.  將適當的索引鍵加入至.pkgdef 檔的 VSPackage。  
  
     例如，以下是 c \+ \+ 語言專案的.pkgdef 設定:  
  
    ```  
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation] "VCProjects"="" [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents] "VCProjectEngineEventsObject"=""  
    ```  
  
2.  實作中的程式碼 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> 方法，如下列範例所示。  
  
    ```cpp  
    STDMETHODIMP CVsPackage::GetAutomationObject( /* [in]  */ LPCOLESTR       pszPropName, /* [out] */ IDispatch **    ppIDispatch) { ExpectedPtrRet(pszPropName); ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (m_fZombie) return E_UNEXPECTED; if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0) { return GetAutomationProjects(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0) { return CAutomationEvents::GetAutomationEvents(ppIDispatch); } return E_INVALIDARG; }   
    ```  
  
     在程式碼的 `g_wszAutomationProjects` 是您的專案集合的名稱。`GetAutomationProjects` 方法會建立該物件會實作 `Projects` 介面，並傳回 `IDispatch` 指標呼叫的物件，如下列程式碼範例所示。  
  
    ```cpp  
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch) { ExpectedPtrRet(ppIDispatch); *ppIDispatch = NULL; if (!m_srpAutomationProjects) { HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects); IfFailRet(hr); ExpectedExprRet(m_srpAutomationProjects != NULL); } return m_srpAutomationProjects.CopyTo(ppIDispatch); }  
    ```  
  
     您應該選擇 automation 物件的唯一名稱。 會產生無法預測，名稱衝突，衝突會導致衝突的物件名稱任意擲回多個專案類型使用相同的名稱。 您應該包含您的公司名稱或唯一的某種程度的 automation 物件的名稱及其產品名稱。  
  
     自訂 `Projects` 集合物件是您專案的自動化模型的其餘部分方便進入點。 您專案的物件是否也可從 <xref:EnvDTE.Solution> 專案集合。 在您建立適當的程式碼和登錄項目可提供與取用者之後 `Projects` 物件集合，您的實作必須提供其餘的專案模型的標準物件。 如需詳細資訊，請參閱[專案模型](../../extensibility/internals/project-modeling.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>