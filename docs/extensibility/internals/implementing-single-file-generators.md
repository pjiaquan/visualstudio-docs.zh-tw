---
title: "實作單一檔案產生器 | Microsoft Docs"
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
  - "實作的自訂工具"
  - "專案 [Visual Studio SDK]，擴充性"
  - "專案 [Visual Studio SDK]，受管理的自訂工具"
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 實作單一檔案產生器
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

自訂工具，有時也稱為單一檔案產生器，可以用來擴充[!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]和[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]專案中的系統[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。  自訂工具是一種 COM 元件實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>介面。  使用這個介面，自訂工具會轉換成單一輸出檔案的單一輸入的檔。  轉換的結果可能是原始碼，或任何其他輸出，是很有用。  自訂工具產生的程式碼檔案的兩個範例是回應在視覺化設計工具和使用 Web 服務描述語言 \(WSDL\) 產生的檔案所做的變更所產生的程式碼。  
  
 當載入自訂工具時，或輸入的檔案儲存時，專案系統會呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A>方法，並將參考傳遞<xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>工具，向使用者報告進度的回呼介面。  
  
 自訂工具所產生的輸出檔案會加入至具有輸入檔相依專案。  專案系統會自動判斷的自訂工具的實作所傳回的字串為基礎的輸出檔案名稱<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>。  
  
 自訂工具必須實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>介面。  自訂工具的支援 \(選擇性\) <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>從輸入檔以外的來源擷取資訊的介面。  在任何情況下，您可以使用自訂的工具之前，則必須登錄它與系統，或在[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]本機登錄。  如需有關如何註冊自訂工具的詳細資訊，請參閱[註冊單一檔案產生器](../../extensibility/internals/registering-single-file-generators.md)。  
  
## 請參閱  
 [判斷專案的預設命名空間](../../misc/determining-the-default-namespace-of-a-project.md)   
 [公開型別，以視覺化設計工具](../../extensibility/internals/exposing-types-to-visual-designers.md)