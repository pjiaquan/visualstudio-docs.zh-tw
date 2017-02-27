---
title: "建立專案類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "新的專案類型"
  - "專案 [Visual Studio SDK]，新專案類型"
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# 建立專案類型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

您可以擴充 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 藉由建立新的專案類型。 若要建立新的專案類型，您必須了解幾個概念，並完成幾個步驟。 下列主題提供如何建立專案類型的概觀。  
  
## 在本節中  
 [專案類型的設計決策](../../extensibility/internals/project-type-design-decisions.md)  
 討論的項目、 專案檔的持續性，並承諾技師修理設計決策，您必須先建立新的專案類型。  
  
 [檢查清單︰ 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)  
 提供建立新的專案類型可支援做為編輯程式碼並編譯、 建置、 偵錯和部署專案中的應用程式的程式設計工作，您必須遵循的步驟的概觀。  
  
 [使用專案 Factory 建立專案](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 提供如何提供，並且使用專案 factory 來建立新專案的執行個體的相關資訊。  
  
 [註冊專案類型](../../extensibility/internals/registering-a-project-type.md)  
 提供程式碼範例的陳述式從登錄提供的預設路徑和資料，以及資料表包含每個陳述式的登錄指令碼中的項目。  
  
 [專案持續性](../../extensibility/internals/project-persistence.md)  
 討論使用 `IPersistFileFormat` 來保存檔案和非檔案型專案物件。  
  
 [使用 MSBuild](../../extensibility/internals/using-msbuild.md)  
 描述如何使用您的專案類型 [!INCLUDE[vstecmsbuild](../../extensibility/internals/includes/vstecmsbuild_md.md)] 建置引擎，讓使用者從建置 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 並在命令列中。  
  
## 相關章節  
 [支援符號瀏覽工具](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 說明程式碼，例如檢視工具的架構 **物件瀏覽器** 和 **類別檢視** 視窗。 描述介面和方法，用於在 VSPackage 中實作瀏覽的物件。  
  
 [加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 討論專案播放決定開啟專案項目時，會使用的編輯器中的重要性，可以管理專案資源的方式。  
  
 [使用 Windows Installer 安裝 Vspackage](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 說明如何為 VSPackage 提供自己的唯一識別碼，以及如何將 VSPackage Dll 和其他資訊包裝在 Windows Installer 套件 \(。MSI 檔案） 以部署至您的客戶。  
  
 [在 Visual Studio 中的階層](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 描述如何 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 檢視和地址的階層。  
  
 [Vspackage](../../extensibility/internals/vspackages.md)  
 提供的 VSPackage，可安裝的 COM 物件延伸概觀 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 環境，並討論如何實作您自己的 VSPackage。  
  
 [專案類型](../../extensibility/internals/project-types.md)  
 討論如何使用專案來修改程式碼、 編譯和建置的程式碼，以及執行和偵錯程式碼，並提供有關如何建立專案類型的詳細主題的連結。