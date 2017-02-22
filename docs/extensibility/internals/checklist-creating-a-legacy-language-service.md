---
title: "檢查清單︰ 建立傳統語言服務 | Microsoft Docs"
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
  - "語言服務"
  - "語言服務，原生程式碼"
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# 檢查清單︰ 建立傳統語言服務
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下列檢查清單摘要說明建立語言服務所必須採取的基本步驟[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]核心編輯器。  若要將您的語言服務區分到[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您必須建立偵錯運算式評估工具。  如需詳細資訊，請參閱[撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)在[Visual Studio 偵錯工具擴充性](../../extensibility/debugger/visual-studio-debugger-extensibility.md)。  
  
## 建立語言服務的步驟  
  
1.  實作 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 介面。  
  
    -   在您的 VSPackage 實作<xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider>文字輸入語言服務。  
  
    -   讓您的語言服務使用整合式的開發環境 \(IDE\) 中您<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>實作。  
  
2.  實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>在主要語言的服務類別的介面。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>介面是核心編輯器和語言服務之間互動的起點。  
  
### 選擇性功能  
 下列功能是選擇性的可以依任何順序執行。  這些功能會增加您的語言服務的功能。  
  
-   語法標色  
  
     實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> 介面。  這個介面的實作應該傳回適當的色彩資訊的剖析器資訊。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A>方法傳回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>介面。  為每個文字緩衝區中，建立個別的 colorizer 執行個體，您應該實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>個別的介面。  如需詳細資訊，請參閱 [語法著色在舊版語言服務](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)。  
  
-   程式碼\] 視窗  
  
     實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>介面，可讓語言服務以接收通知中建立新的 \[程式碼\] 視窗時。  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A>方法傳回<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>介面。  語言服務接著可以新增至 \[程式碼\] 視窗中的特殊 UI <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>。  語言服務也可以執行任何特殊處理，例如新增文字檢視篩選條件，在<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>。  
  
-   文字檢視篩選條件  
  
     若要提供 IntelliSense 陳述式完成語言服務中的，您必須攔截部分文字檢視會處理的指令。  若要攔截這些命令，完成下列步驟：  
  
    -   實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>參與命令鏈結，控制代碼編輯器命令。  
  
    -   呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法，並傳入您<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>實作。  
  
    -   呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A>方法，當您中斷連結\] 檢視中使這些命令不會再傳送給您。  
  
     必須處理的命令是根據所提供的服務而定。  如需詳細資訊，請參閱 [語言服務篩選器的重要命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>必須為相同的物件上實作介面<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>介面。  
  
-   陳述式完成  
  
     實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> 介面。  
  
     支援的陳述式完成指令 \(也就是<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>\)，並呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>中的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>介面，傳遞<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>介面。  如需詳細資訊，請參閱 [在舊版語言服務中的陳述式完成](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)。  
  
-   方法秘訣  
  
     實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>介面，以提供資料給方法的 \[提示\] 視窗。  
  
     安裝文字檢視篩選條件，來適當處理命令，讓您知道何時要顯示的方法資料提示視窗。  如需詳細資訊，請參閱 [在舊版語言服務中的參數資訊](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)。  
  
-   錯誤標記  
  
     實作 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> 介面。  
  
     建立實作的標記物件的錯誤碼<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面和呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法，傳遞<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>錯誤標記物件的介面。  
  
     通常每個錯誤標記管理 \[工作清單\] 視窗中的項目。  
  
-   工作清單項目  
  
     實作工作項目類別提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem>介面。  
  
     實作工作提供者類別提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider>介面和<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>介面。  
  
     實作工作列舉值類別提供<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems>介面。  
  
     註冊工作清單\] 的工作提供者<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A>方法。  
  
     取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>介面，藉由呼叫服務 GUID 的語言服務的服務提供者<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>。  
  
     建立工作項目物件和呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A>中的方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList>介面，當有新或更新的任務。  
  
-   註解工作項目  
  
     使用<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>介面和<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>介面，以取得註解工作語彙基元。  
  
     取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo>介面從<xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>服務。  
  
     取得<xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens>介面從<xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A>方法。  
  
     實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents>介面，以接聽語彙基元的清單中的變更。  
  
-   大綱  
  
     有許多選項來支援大綱。  例如，您也可以支援**摺疊至定義**命令，提供編輯器控制的大綱區域，或支援用戶端控制的區域。  如需詳細資訊，請參閱 [如何︰ 展開大綱中提供支援舊版語言服務](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)。  
  
-   語言服務註冊  
  
     如需有關如何註冊語言服務的詳細資訊，請參閱[註冊舊版語言服務](../../extensibility/internals/registering-a-legacy-language-service2.md)和[管理 Vspackage](../../extensibility/managing-vspackages.md)。  
  
-   即時線上說明  
  
     提供給編輯器\] 中的內容，下列方法之一：  
  
    -   提供文字標記中的內容，藉由實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>介面。  
  
 提供所有的使用者內容，藉由實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider>介面。  
  
## 請參閱  
 [開發語言服務](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [撰寫 CLR 運算式評估工具](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)