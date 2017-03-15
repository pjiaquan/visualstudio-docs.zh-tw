---
title: "建立自訂編輯器和設計工具 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "設計工具 [Visual Studio SDK]"
  - "編輯器 [Visual Studio SDK] 自訂"
ms.assetid: b6a5e8b2-0ae1-4fc3-812d-09d40051b435
caps.latest.revision: 31
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 31
---
# 建立自訂編輯器和設計工具
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio 整合式的開發環境 \(IDE\) 可以裝載不同類型的編輯器:  
  
-   Visual Studio 核心編輯器  
  
-   自訂編輯器  
  
-   外部編輯器  
  
-   設計工具  
  
 下列資訊可協助您選擇的編輯器，您需要的類型。  
  
## 類型的編輯器  
 Visual Studio 核心編輯器的相關資訊，請參閱 [擴充編輯器和語言服務](../extensibility/extending-the-editor-and-language-services.md)。  
  
##### 自訂編輯器  
 自訂編輯器是設計成只能在特定情況下。 例如，您可以建立函式是以讀取和寫入資料至特定的儲存機制，例如 Microsoft Exchange server 的編輯器。 如果您想要編輯器可與您的專案類型只使用，或如果您想要編輯器，只有少數的特定命令，請選擇自訂編輯器。 請注意，不過，使用者不能使用自訂的編輯器編輯標準 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 專案。  
  
 使用編輯器 factory 自訂編輯器，並將編輯器\] 中的相關資訊新增至登錄。 不過，自訂編輯器相關聯的專案類型可以具現化中的其他方法的自訂編輯器。  
  
 自訂編輯器，可以使用就地啟動或簡化的嵌入實作檢視。  
  
##### 外部編輯器  
 外部編輯器都不會整合至 Visual Studio 中，例如 Microsoft Word 中，\[記事本\] 或 Microsoft FrontPage 的編輯器。 如果，例如，您要它傳遞文字從 VSPackage，您可能會呼叫這類的編輯器。 外部編輯器自行註冊，並可使用 Visual Studio 外部。 當您呼叫外部編輯器中，可以內嵌在主視窗中，會出現在 IDE 中的視窗。 如果沒有，IDE 然後為其建立另一個視窗。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 方法會設定文件的優先順序使用 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 列舉型別。 如果 `DP_External` 值指定，則可以透過外部的編輯器開啟檔案。  
  
## 編輯器的設計決策  
 下列的設計問題可協助您選擇適合您的應用程式的最佳編輯器類型:  
  
-   將您的應用程式儲存其資料檔案中或不嗎? 如果它會將其資料儲存在檔案中，它們會以自訂或標準格式?  
  
     如果您使用標準檔案格式，除了您的專案的其他專案類型可以開啟和讀取\/寫入資料到它們。 如果您使用自訂檔案格式，不過，只有您的專案類型將能夠開啟和讀取\/寫入資料到它們。  
  
     如果您的專案使用的檔案，您應該自訂之標準編輯器。 如果您的專案不會使用檔案，但使用的資料庫或其他儲存機制中的項目，您應該建立自訂編輯器。  
  
-   您的編輯器需要裝載 ActiveX 控制項嗎?  
  
     如果您的編輯器裝載 ActiveX 控制項，然後實作就地啟動編輯器中所述 [就地啟動](../misc/in-place-activation.md)。 如果它不會裝載 ActiveX 控制項，然後使用簡化的嵌入編輯器中，或自訂 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 預設編輯器。  
  
-   將您的編輯器支援多個檢視? 如果您想要看到的預設編輯器，同時您編輯器的檢視，您必須支援多個檢視。  
  
     如果您的編輯器需要支援多個檢視，編輯器\] 中的文件檢視物件與文件資料必須是不同的物件。 如需詳細資訊，請參閱[支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。  
  
     如果您的編輯器支援多個檢視，請執行您打算使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 核心編輯器的文字緩衝區實作 \(<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 物件\) 的文件資料物件? 也就是您想支援您編輯器檢視\-並存使用 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 核心編輯器? 若要執行這項操作的能力是表單設計工具的基礎...  
  
-   如果您需要裝載外部編輯器時，編輯器可以內嵌內 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]嗎?  
  
     如果可以內嵌，您應該為外部編輯器建立主應用程式視窗，然後呼叫 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A> 方法，並設定 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 列舉值，以 `DP_External`。 如果無法內嵌編輯器，IDE 會自動為它建立個別的視窗。  
  
## 本章節內容  
 [逐步解說: 建立自訂編輯器](../extensibility/walkthrough-creating-a-custom-editor.md)  
 說明如何建立自訂編輯器。  
  
 [逐步解說 ︰ 加入功能與自訂編輯器](../extensibility/walkthrough-adding-features-to-a-custom-editor.md)  
 說明如何將功能加入至自訂編輯器。  
  
 [設計工具的初始設定和中繼資料組態](../extensibility/designer-initialization-and-metadata-configuration.md)  
 說明如何初始化設計工具。  
  
 [提供復原功能給設計工具支援](../extensibility/supplying-undo-support-to-designers.md)  
 說明如何設計工具提供復原功能支援。  
  
 [語法著色中自訂編輯器](../extensibility/syntax-coloring-in-custom-editors.md)  
 說明語法色彩編碼在核心編輯器和自訂編輯器之間的差異。  
  
 [文件資料，以及在自訂編輯器中的文件檢視](../extensibility/document-data-and-document-view-in-custom-editors.md)  
 說明如何實作自訂編輯器中的文件資料和文件的檢視。  
  
## 相關章節  
 [在編輯器中的傳統介面](../extensibility/legacy-interfaces-in-the-editor.md)  
 說明如何透過舊版 API 存取核心編輯器。  
  
 [開發語言服務](../extensibility/internals/developing-a-legacy-language-service.md)  
 說明如何實作語言服務。  
  
 [擴充 Visual Studio 的其他部分](../extensibility/extending-other-parts-of-visual-studio.md)  
 說明如何建立符合其餘的 UI 項目 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>