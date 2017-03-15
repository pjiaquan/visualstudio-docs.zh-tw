---
title: "VisibilityItem 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VisibilityItem 項目 (VSCT XML 結構描述)"
  - "VisibilityItem，VSCT XML 結構描述項目"
ms.assetid: 0932f551-972d-4194-84bb-426e3e4375e4
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# VisibilityItem 項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

`VisibilityItem` 元素會決定靜態命令和工具列的可見性。 每個項目識別命令或\] 功能表上，以及相關聯的命令 UI 的內容。 Visual Studio 會偵測命令、 功能表和工具列和可見性，而不載入 Vspackage 定義它們。 IDE 會使用 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A> 方法，以判斷命令 UI 內容是否在使用中。  
  
 載入 VSPackage 後，Visual Studio 必須要有命令的 VSPackage 所決定的可見性而 `VisibilityItem`。 若要判斷命令的可見性，您可以實作 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus> 事件處理常式或 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> 方法，會根據您如何實作您的命令。  
  
 命令或包含 `VisibilityItem` 項目會顯示只有當關聯的內容在作用中。 您可以包括每個命令內容組合的項目，來建立單一命令、 功能表或工具列關聯具有一個或多個命令 UI 的內容。 如果命令或功能表是多個命令 UI 內容相關聯，然後命令或功能表會顯示相關聯的命令 UI 任何的內容一個使用中時。  
  
 `VisibilityItem` 項目只適用於命令、 功能表和工具列，不到群組。 沒有相關的項目 `VisibilityItem` 項目是可見的只要其父功能表。  
  
## 語法  
  
```  
<VisibilityItem  
  guid ="="cmdGuidMyProductCommands"  
  id=="cmdidAddWidget"  
  context="guidNotViewSourceMode"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|guid|必要項。 GUID ID 的命令識別項的 GUID。|  
|id|必要項。 GUID ID 的命令識別項的識別碼。|  
|內容|必要項。 此命令會顯示 UI 內容。|  
|條件|選擇項。 請參閱 [條件式屬性](../extensibility/vsct-xml-schema-conditional-attributes.md)。|  
  
### 子項目  
 無  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[VisibilityConstraints 項目](../extensibility/visibilityconstraints-element.md)|`VisibilityConstraints` 項目決定靜態群組的命令和工具列是否可見。|  
  
## 備註  
 中所定義的標準 Visual Studio UI 內容 *Visual Studio SDK 安裝路徑*\\VisualStudioIntegration\\Common\\Inc\\vsshlids.h 檔案以及與 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids> 和 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> 類別。 一組更完整的 UI 內容定義於 <xref:Microsoft.VisualStudio.VSConstants> 類別。  
  
## 範例  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.IsCmdUIContextActive%2A>   
 <xref:Microsoft.VisualStudio.Shell.OleMenuCommand.BeforeQueryStatus>   
 <xref:Microsoft.VisualStudio.VSConstants>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids>   
 <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80>   
 [VisibilityConstraints 項目](../extensibility/visibilityconstraints-element.md)   
 [Visual Studio 命令資料表 \(。Vsct\) 檔案](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)