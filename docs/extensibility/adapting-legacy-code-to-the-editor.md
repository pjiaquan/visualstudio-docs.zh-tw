---
title: "調整舊版程式碼編輯器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版的配接器"
ms.assetid: a208d38e-9bea-41c9-9fe2-38bd86a359cb
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 調整舊版程式碼編輯器
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

在 Visual Studio 編輯器有許多功能，您可以從現有的程式碼元件存取。 下列指示說明如何修改非 MEF 元件，例如 VSPackage，若要使用編輯器功能。 指示也會示範如何使用配接器取得 managed 和 unmanaged 程式碼中的編輯器\] 中的服務。  
  
## 編輯器配接器  
 編輯器的介面卡，或是填充碼是包裝函式也會公開的類別和介面中的編輯器物件 <xref:Microsoft.VisualStudio.TextManager.Interop> API。 您可以使用的配接器，例如非編輯器服務之間移動，Visual Studio shell 命令，編輯器服務。 （這是編輯器\] 中目前如何裝載在 Visual Studio 中）。 配接器也會啟用傳統編輯器和語言服務擴充功能在 Visual Studio 中正常運作。  
  
## 使用編輯器配接器  
 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> 提供新的編輯器介面和舊版的介面之間切換的方法，也建立配接器的方法。  
  
 如果您在 MEF 元件組件使用此服務，可以匯入服務，如下所示。  
  
```  
[Import(typeof(IVsEditorAdaptersFactoryService))]  
internal IVsEditorAdaptersFactoryService editorFactory;  
```  
  
 如果您想要在非 MEF 元件中使用這項服務，請遵循本主題後面的 \< 使用 Visual Studio 編輯器服務在非 MEF 元件 \> 一節中的指示。  
  
## 新的編輯器 API 和舊版 API 之間切換  
 使用下列方法切換編輯器物件和傳統的介面。  
  
|方法|轉換|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetBufferAdapter%2A>|將轉換 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 到 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDataBuffer%2A>|將轉換 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 到 <xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetDocumentBuffer%2A>|將轉換 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 到 <xref:Microsoft.VisualStudio.Text.ITextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetViewAdapter%2A>|將轉換 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> 到 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.GetWpfTextView%2A>|將轉換 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 到 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>。|  
  
## 建立配接器  
 使用下列方法建立的舊版介面的配接器。  
  
|方法|轉換|  
|--------|--------|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsCodeWindowAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> 指定 <xref:Microsoft.VisualStudio.Utilities.IContentType>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextBufferCoordinatorAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBufferCoordinator>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 的 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewRoleSet>。|  
|<xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService.CreateVsTextViewAdapter%2A>|建立 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>。|  
  
## Unmanaged 程式碼中建立配接器  
 所有配接器類別會註冊為本地共同建立，而且可以使用具現化 `VsLocalCreateInstance()` 函式。  
  
 使用中的 vsshlids.h 檔案中所定義的 Guid 來建立所有介面卡...Visual Studio SDK 安裝的 \\VisualStudioIntegration\\Common\\Inc\\ 資料夾。 若要建立 VsTextBufferAdapter 的執行個體，請使用下列程式碼。  
  
```  
IVsTextBuffer *pBuf = NULL;  
VsLocalCreateInstance(CLSID_VsTextBuffer, NULL, CLSCTX_INPROC_SERVER, IID_IVsTextBuffer, (void**)&pBuf);  
```  
  
## 在 Managed 程式碼建立配接器  
 在 managed 程式碼，您可以共同建立配接器所述的 unmanaged 程式碼相同的方式。 您也可以使用 MEF 服務，可讓您建立和使用配接器互動。 取得配接器的這種方式可讓您更細微地控制超過您擁有共同建立時。  
  
#### 若要建立 IVsTextView 配接器  
  
1.  加入 Microsoft.VisualStudio.Editor.dll 的參考。 請確定 `CopyLocal` 設為 `false`。  
  
2.  具現化 <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, 、，如下所示。  
  
    ```  
    using Microsoft.VisualStudio.Editor;  
    ...  
    IVsEditorAdaptersFactoryService adapterFactoryService = ComponentModel.GetService<IVsEditorAdaptersFactoryService>();  
    ```  
  
3.  呼叫 `CreateX()` 方法。  
  
    ```  
    adapterFactoryService.CreateTextViewAdapter(textView);  
    ```  
  
## 使用 Visual Studio 編輯器中直接從 Unmanaged 程式碼  
 Microsoft.VisualStudio.Platform.VSEditor 命名空間和 Microsoft.VisualStudio.Platform.VSEditor.Interop 命名空間，做為 IVx \* 介面公開 COM 可呼叫的介面。 例如，Microsoft.VisualStudio.Platform.VSEditor.Interop.IVxTextBuffer 介面是 COM 版本 <xref:Microsoft.VisualStudio.Text.ITextBuffer> 介面。 從 `IVxTextBuffer`, ，您可以取得緩衝區快照集的存取權、 緩衝區的修改，接聽緩衝區上的文字變更事件並建立追蹤點和範圍。 下列步驟示範如何存取 `IVxTextBuffer` 從 `IVsTextBuffer`。  
  
#### 若要取得 IVxTextBuffer  
  
1.  IVx \* 介面的定義是 VSEditor.h 檔案中...Visual Studio SDK 安裝的 \\VisualStudioIntegration\\Common\\Inc\\ 資料夾。  
  
2.  下列程式碼會具現化文字緩衝區使用 `IVsUserData->GetData()` 方法。 下列程式碼， `pData` 是指向 `IVsUserData` 物件。  
  
    ```  
    #include <textmgr.h>  
    #include <VSEditor.h>  
    #include <vsshlids.h>  
  
    CComPtr<IVsTextBuffer> pVsTextBuffer;  
    CComPtr<IVsUserData> pData;  
    CComPtr<IVxTextBuffer> pVxBuffer;  
    ...  
    if (SUCCEEDED(pVsTextBuffer->QueryInterface(IID_IVsUserData, &pData))  
    {  
        CComVariant vt;  
        if (SUCCEEDED(pData->GetData(GUID_VxTextBuffer, &vt)) &&  
        (vt.Type == VT_UNKNOWN) && (vt.punkVal != NULL))  
        {  
            vt.punkVal->QueryInterface(IID_IVxTextBuffer, (void**)&pVxBuffer);  
        }  
    }  
    ```  
  
## 使用 Visual Studio 編輯器服務在非 MEF 元件  
 如果您有現有的 managed 程式碼元件不會使用 MEF，而且您想要使用 Visual Studio 編輯器中的服務，您必須加入包含 ComponentModelHost VSPackage 的組件的參考，並取得其 SComponentModel 服務。  
  
#### 若要使用 Visual Studio 編輯器元件從非 MEF 元件  
  
1.  將參考加入 Microsoft.VisualStudio.ComponentModelHost.dll 組件中...Visual Studio 安裝的 \\Common7\\IDE\\ 資料夾。 請確定 `CopyLocal` 設為 `false`。  
  
2.  加入私用 `IComponentModel` 您要使用 Visual Studio 編輯器服務，如下所示的類別的成員。  
  
    ```  
    using Microsoft.VisualStudio.ComponentModelHost;  
    ....  
    private IComponentModel componentModel;  
    ```  
  
3.  具現化元件模型，您的元件的初始化方法中。  
  
    ```  
    componentModel =  
     (IComponentModel)Package.GetGlobalService(typeof(SComponentModel));  
    ```  
  
4.  在此之後，您可以藉由呼叫取得 Visual Studio 編輯器服務的任何一個 `IComponentModel.GetService<T>()` 服務您想要的方法。  
  
    ```  
    textBufferFactoryService =  
         componentModel.GetService<ITextBufferFactoryService>();     
    ```