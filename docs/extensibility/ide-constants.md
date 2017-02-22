---
title: "IDE 常數 | Microsoft Docs"
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
  - "IDE 錯誤"
  - "邏輯檢視"
  - "錯誤 [Visual Studio] IDE"
  - "UI 內容常數"
  - "常數，Visual Studio IDE"
  - "IDE 常數"
  - "實體檢視"
ms.assetid: 5030e70a-241d-474a-ba8c-e3b1cf947ff0
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# IDE 常數
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

<xref:Microsoft.VisualStudio.VSConstants> 類別會提供的常數只可在整合式的開發環境 \(IDE\) 和先前定義只在標頭檔中。  
  
## 邏輯和實體檢視  
  
|值|描述|  
|-------|--------|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式應該傳遞此值以 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法來取得 **開啟** 對話方塊中，在此情況下，在可能的程式碼檢視。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式會傳遞此值以 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法來取得 **開啟** 對話方塊中，在此情況下填入可能 <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Debugging> 偵錯與檢視不同的對應檢視 <xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Code>。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Designer>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式會傳遞此值以 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法來取得 **開啟** 對話方塊中的，在此例中 **檢視表單** 設計工具檢視。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_Primary>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式會傳遞此值以 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法來取得 **開啟** 對話方塊中，在此情況下編輯器 factory 的預設\/主要檢視。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_TextView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式會傳遞此值以 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法來取得 **開啟** 對話方塊中，在此文件或資料的文字編輯器檢視。|  
|<xref:Microsoft.VisualStudio.VSConstants.LOGVIEWID_UserChooseView>|<xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> `cmdidOpenWith` 處理常式會傳遞此值以 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 方法，系統會提示使用者選擇要使用哪一個使用者定義的檢視。|  
  
## 編輯器 Factory 旗標  
  
|值|描述|  
|-------|--------|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>|過時的旗標位元的第一個參數的結合 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 方法。|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENASNEW>|組合的位元的第一個參數為 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A>, ，這個方法，指出編輯器 factory 應該執行必要的修正程式。|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_OPENFILE>|組合的位元的第一個參數為 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 方法，這個旗標是互斥的 exclusive <xref:Microsoft.VisualStudio.VSConstants.CEF_CLONEFILE>。|  
|<xref:Microsoft.VisualStudio.VSConstants.CEF_SILENT>|組合的位元的第一個參數為 <xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 方法，這會指示編輯器 factory 應該建立編輯器\] 中，而不顯示使用者介面 \(UI\)。|  
  
## Visual Studio 的 \[錯誤  
  
|值|描述|  
|-------|--------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_BUSY>|傳回介面的非同步行為常數時在該物件中已忙碌|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>|錯誤的特定 HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的 「 不相容的文件資料 」。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PACKAGENOTLOADED>|錯誤的特定 HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，並指出 「 無法載入封裝 」。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTALREADYEXISTS>|錯誤的特定 HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，並指出，「 專案已經存在 」|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTMIGRATIONFAILED>|錯誤的特定 HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，並指出 「 專案組態失敗 」。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_PROJECTNOTLOADED>|錯誤的特定 HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，並指出 「 無法載入專案 」。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONALREADYOPEN>|錯誤的特定 HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，並指出 「 解決方案已經開啟。 」|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SOLUTIONNOTOPEN>|錯誤的特定 HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，並指出 「 解決方案未開啟。 」|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_SPECIFYING_OUTPUT_UNSUPPORTED>|傳回所具有的參數來指定陣列中的組建介面 <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput> 介面，但在實作僅適用於該方法的所有輸出。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>|<xref:Microsoft.VisualStudio.Package.EditorFactory.CreateEditorInstance%2A> 方法會傳回此值，如果文件無法在編輯器中開啟的格式。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_E_WIZARDBACKBUTTONPRESS>|HRESULT 值，指出使用者叫用中的上一頁按鈕 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 精靈。|  
  
## Visual Studio 常數  
  
|值|描述|  
|-------|--------|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_PROJECTFORWARDED>|錯誤的特定 HRESULT [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，並指出 「 專案轉送 」。|  
|<xref:Microsoft.VisualStudio.VSConstants.VS_S_TBXMARKER>|常數的特定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 的 「 工具箱標記 」。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_ENTERMODAL>|常數的特定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 廣播通知訊息透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 方法表示的樣式開頭。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_EXITMODAL>|常數的特定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 廣播通知訊息透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 方法，表示樣式的結尾。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSM_TOOLBARMETRICSCHANGE>|常數的特定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 廣播通知訊息透過 <xref:Microsoft.VisualStudio.Shell.Interop.IVsBroadcastMessageEvents.OnBroadcastMessage%2A> 指出已變更的命令列度量資訊的方法。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSCOOKIE_NIL>|常數的特定 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，表示尚未設定 cookie。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_NIL>|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 代表專案項目不存在的項目識別項。 目前的選取範圍時，會使用此值。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_ROOT>|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 代表專案階層架構的根目錄，並可用來識別，而不是單一項目在整個階層的項目識別項。|  
|<xref:Microsoft.VisualStudio.VSConstants.VSITEMID_SELECTION>|A [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ，表示目前選取的項目或項目，可以包含階層的根項目識別項。|  
  
## IVsSelectionEvents  
 描述 IDE 的哪個元件只是已選取，在 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents.OnElementValueChanged%2A> 呼叫，例如。  
  
|常數|值|  
|--------|-------|  
|<xref:Microsoft.VisualStudio.VSConstants.DocumentFrame>|0x2|  
|<xref:Microsoft.VisualStudio.VSConstants.PropertyBrowserSID>|0x4|  
|<xref:Microsoft.VisualStudio.VSConstants.StartupProject>|0x3|  
|<xref:Microsoft.VisualStudio.VSConstants.UndoManager>|0x0|  
|<xref:Microsoft.VisualStudio.VSConstants.UserContext>|0x5|  
|<xref:Microsoft.VisualStudio.VSConstants.WindowFrame>|0x1|  
  
## VSSELELEMID  
 常數用來指出新的選取狀態。  
  
|常數|值|  
|--------|-------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|2|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|7|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|4|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|6|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|3|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|0|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|5|  
|<xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID>|1|  
  
## 元件選取器對話方塊常數  
  
|常數|值|  
|--------|-------|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELCHANGED>|WM\_USER 1280 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPDN_SELDBLCLICK>|WM\_USER 1281 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_CLEARSELECTION>|WM\_USER 1290 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_GETSELECTION>|WM\_USER 1287 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZELIST>|WM\_USER 1285 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_INITIALIZETAB>|WM\_USER 1288 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_QUERYCANSELECT>|WM\_USER 1286 \+|  
|<xref:Microsoft.VisualStudio.VSConstants.CPPM_SETMULTISELECT>|WM\_USER 1289 \+|  
  
## 請參閱  
 [IDE 定義的命令，來擴充專案系統](../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)