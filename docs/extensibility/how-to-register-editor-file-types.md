---
title: "如何: 登錄編輯程式檔案類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版的登錄檔案類型"
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 如何: 登錄編輯程式檔案類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

登錄編輯器的檔案類型最簡單的方法是使用所提供的一部份的註冊屬性[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]管理套件架構 \(MPF\) 類別。  如果您正在實作包裝在原生[!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]，您也可以寫入登錄您的編輯器及相關的擴充程式的登錄指令檔。  
  
## 使用 MPF 類別的註冊  
  
#### 若要註冊使用 MPF 類別的檔案類型編輯器  
  
1.  提供<xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>與您的編輯器，在您的 VSPackage 類別中的適當參數的類別。  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     其中"。Sample"為擴充程式註冊為這個編輯器\] 中，而"32"是它的優先順序等級。  
  
     `projectGuid`中所定義的其他檔案類型的 guid 的<xref:Microsoft.VisualStudio.VSConstants.CLSID_MiscellaneousFilesProject>。  提供的其他檔案類型，以便產生的檔案並不在建置程序的一部分。  
  
     `TemplateDir`表示包含隨附於受管理的基本編輯器範例的範本檔案的資料夾。  
  
     `NameResourceID`定義在 Resources.h 檔案中的 \[BasicEditorUI\] 專案，並指出編輯器\] 中做為 「 我的編輯器 」。  
  
2.  覆寫 <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> 方法。  
  
     在實作中的<xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>方法，請打<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>方法，並傳遞做為您編輯器工廠的執行個體所示如下。  
  
    ```  
    protected override void Initialize()  
    {  
        Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,   
        "Entering Initialize() of: {0}", this.ToString()));  
        base.Initialize();  
           //Create Editor Factory  
        editorFactory = new EditorFactory(this);  
        base.RegisterEditorFactory(editorFactory);  
    }  
    ```  
  
     這個步驟會登錄編輯器工廠和編輯器的副檔名。  
  
3.  解除登錄編輯器的工廠。  
  
     VSPackage 處置時，會自動取消登錄編輯器工廠。  如果編輯器工廠物件實作<xref:System.IDisposable>介面，其`Dispose`會呼叫之後使用，已解除登錄工廠[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## 使用登錄指令碼的登錄  
 登錄編輯器工廠和檔案類型，在原生[!INCLUDE[vcprvc](../debugger/includes/vcprvc_md.md)]完成寫入 windows 登錄中，使用登錄指令碼，如以下圖解所示。  
  
#### 若要註冊使用登錄指令碼的檔案類型編輯器  
  
1.  在您的登錄指令碼，定義編輯器原廠 」 和 「 編輯器工廠 GUID 字串中所示`GUID_BscEditorFactory`一節的下列的登錄指令碼。  此外，定義的擴充和編輯器延伸模組的優先順序：  
  
    ```  
  
                NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0  
  
            LogicalViews  
            {  
                val %LOGVIEWID_TextView% = s ''  
            }  
  
            OpenWithEntries  
            {  
            }  
  
            Extensions             {                 val rtf = d 50             }  
        }  
    }  
    ```  
  
     編輯器的檔案副檔名，在此範例便會被視為".rtf"，其優先順序為 「 50 」。  BscEdit 範例專案 Resource.h 檔中定義 GUID 字串。  
  
2.  註冊的 VSPackage。  
  
3.  登錄編輯器工廠。  
  
     編輯器處理站已登錄在<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>實作。  
  
    ```  
    // create editor factory.  
    if (m_srpEdFact == NULL)   
    {  
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;  
        if (NULL == pEdFact)  
          return E_OUTOFMEMORY;  
  
        if (!pEdFact->FInit(this))  
          return E_UNEXPECTED;  
  
        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()  
    }  
    // Query service for IVsRegisterEditors, register the editor factory  
    CComPtr<IVsRegisterEditors> srpRegEd;  
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))  
      {  
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));  
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,  
                      m_srpEdFact, &m_dwEditorCookie)))   
          {  
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));  
            return E_FAIL;  
          }  
      }  
        return S_OK;  
    }  
    ```  
  
     在 BscEdit 專案的 Resource.h 檔中定義 GUID 字串。