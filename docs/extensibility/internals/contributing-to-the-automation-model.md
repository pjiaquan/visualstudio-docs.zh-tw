---
title: "提供 Automation 模型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自動化 [Visual Studio SDK]"
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 提供 Automation 模型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Visual Studio 會提供一組自動化介面的自訂環境。 Automation 模型是可讓使用者建立 Visual Studio 增益集和擴充功能的物件模型。  
  
 此外，它很適合您，VSPackage 開發人員參與自動化模型;如此一來，您啟用使用者的 VSPackage 建立增益集，並使用您的 VSPackage 中時，通常提供使用者呈現一致的模型 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
 若要讓一般使用者經驗一致，您可以遵循一組的指導方針，讓您 VSPackage 的 automation 模型會遵循在概念設計 VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  
  
## 在本節中  
 [自動化模型概觀](../../extensibility/internals/automation-model-overview.md)  
 Automation 模型定義之物件的控制主要面向，常見的環境的相關群組。 這組物件，如圖中自動化模型的圖表所示。  
  
 [提供自動化的 Vspackage](../../extensibility/internals/providing-automation-for-vspackages.md)  
 討論兩種主要方式，並提供自動化的 VSPackage。  
  
 [公開專案物件](../../extensibility/internals/exposing-project-objects.md)  
 提供建立 VSPackage 特有之物件的逐步指示。  
  
 [專案模型](../../extensibility/internals/project-modeling.md)  
 說明建立新的專案類型的自動化所需的標準專案物件，並說明專案自動化遵循的路徑。 本主題也提供宣告和實作類別的清單。  
  
 [公開事件](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)  
 提供建立事件的 automation 模型的逐步指示。  
  
 [在選項頁面的自動化支援](../../extensibility/internals/automation-support-for-options-pages.md)  
 描述如何傳回對 automation 物件支援的 VSPackage 屬性的自訂 **選項** 對話方塊 **工具** 延伸功能表 `DTE.Properties` 物件。  
  
 [提供自動化的程式碼](../../extensibility/internals/providing-automation-for-code.md)  
 說明，建立自動化模型的程式碼並不需要。 不過，提供程式碼模型的詳細資訊，本主題中提供的連結。  
  
 [如何: 提供適用於 Windows 的自動化](../../extensibility/internals/how-to-provide-automation-for-windows.md)  
 說明提供自動化是個好主意每當您想要在視窗中，使用 automation 物件和環境已經不提供現成的自動化物件。 討論自動化的工具視窗與文件視窗。  
  
 [使用自動化模型](../../extensibility/internals/using-the-automation-model.md)  
 提供兩個程式碼範例示範如何自動化取用者會取得初始專案 automation 物件。  
  
 [自動化的組態和 SelectedItem 物件](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)  
 提供組態選項的自動化和自動化的選取項目相關資訊。  
  
## 參考  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>  
 提供的程式碼範例示範如何在 VSPackage 參與 DTE automation 物件模型。 列出參數、 傳回值，以及所選的 \< 備註 \>。  
  
## 相關章節