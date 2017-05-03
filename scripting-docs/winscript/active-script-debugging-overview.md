---
title: "動態指令碼偵錯概觀 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "動態指令碼偵錯概觀"
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# 動態指令碼偵錯概觀
現用指令碼偵錯介面允許語言中性，主應用程式中性偵錯，並支援各種開發環境。  
  
 ![Script Host 程序](../winscript/media/scp56activdbgarchgif.png "Scp56ActivDbgArchgif")  
圖 1  
  
 語言中性偵錯環境可以支援程式設計語言中的所有程式語言或混合，，不需要有特定的知識任何語言。  偵錯環境也支援跨語言逐步執行和中斷點。  \(這個概觀著重於主要支援的指令碼語言，例如 VBScript 和 [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]\)。  
  
 主機是偵錯工具可以自動使用任何 Active Scripting 主機，例如 Internet Explorer 或自訂主應用程式。  主控制項哪些偵錯工具呈現給使用者，從文件樹狀結構進行偵錯之內容和語法標色文件。  這可讓偵錯的原始程式碼會顯示在主應用程式文件中。  例如， Internet Explorer 在 HTML 網頁可以顯示指令碼。  
  
 下列小節，作用中偵錯的每個主要元件及其關聯的介面中討論。  不過，在未來發生前，數按鍵作用中偵錯概念必須定義:  
  
 Host Application \- 主應用程式  
 裝載指令碼引擎並提供可編寫指令碼物件集的應用程式 \(或物件模型」\)。  
  
 語言引擎  
 提供剖析的元件，執行，而且偵錯特定語言的抽象。  
  
 偵錯工具 IDE  
 透過通訊提供偵錯 UI 與主應用程式和語言引擎的應用程式。  
  
 電腦偵錯管理員  
 維護偵錯應用程式處理序已註冊元件。  
  
 處理序偵錯管理員  
 維護偵錯文件樹狀結構中特定應用程式的元件，追蹤的執行緒，依此類推。  
  
 資料內容  
 資料內容是代表在主應用程式文件的原始程式碼的抽象特定範圍。  
  
 程式碼內容  
 程式碼內容表示語言引擎 \(「虛擬指令指標」的循序程式碼中的特定位置\)。  
  
 運算式內容。  
 特定內容 \(例如，堆疊框架\) 運算式可以由語言引擎評估。  
  
 瀏覽的物件  
 物件名稱的結構化，和語言無關的表示，型別、值和子物件，適用於實作「監看式視窗」UI。  
  
 下列每個概觀主要作用中偵錯元件和對應，關聯的介面，接著為這些介面詳細資料。  
  
## 語言引擎  
 語言引擎提供:  
  
-   語言剖析和執行。  
  
-   偵錯支援 \(中斷點等等\)。  
  
-   運算式評估。  
  
-   語法標色。  
  
-   瀏覽的物件。  
  
-   堆疊列舉和剖析。  
  
 下列指令碼引擎必須支援的偵錯、瀏覽運算式評估和物件的介面。  主應用程式使用這些介面要將其資料內容和引擎的程式碼內容之間，以及由做運算式評估堆疊、列舉型別和物件的偵錯工具 UI 瀏覽。  
  
 [IActiveScriptDebug 介面](../winscript/reference/iactivescriptdebug-interface.md)  
 提供語法標色和程式碼內容列舉。  
  
 [IActiveScriptErrorDebug 介面](../winscript/reference/iactivescripterrordebug-interface.md)  
 傳回資料內容和堆疊框架錯誤的。  
  
 [IActiveScriptSiteDebug 介面](../winscript/reference/iactivescriptsitedebug-interface.md)  
 主應用程式提供了連結從指令碼引擎到偵錯工具。  
  
 [IDebugCodeContext 介面](../winscript/reference/idebugcodecontext-interface.md)  
 提供虛擬「指令指標」中的執行緒。  
  
 [IEnumDebugCodeContexts 介面](../winscript/reference/ienumdebugcodecontexts-interface.md)  
 列舉型別對應至資料內容的程式碼內容。  
  
 [IDebugStackFrame 介面](../winscript/reference/idebugstackframe-interface.md)  
 表示在執行緒堆疊的邏輯堆疊框架。  
  
 [IDebugExpressionContext 介面](../winscript/reference/idebugexpressioncontext-interface.md)  
 提供運算式可以評估的內容。  
  
 [IDebugStackFrameSniffer 介面](../winscript/reference/idebugstackframesniffer-interface.md)  
 提供列舉邏輯堆疊框架。  
  
 [IDebugExpression 介面](../winscript/reference/idebugexpression-interface.md)  
 表示非同步評估的運算式。  
  
 [IDebugSyncOperation 介面](../winscript/reference/idebugsyncoperation-interface.md)  
 允許指令碼引擎擷取特定封鎖的執行緒時需要執行，在巢狀的作業。  
  
 [IDebugAsyncOperation 介面](../winscript/reference/idebugasyncoperation-interface.md)  
 提供同步處理非同步存取偵錯作業。  
  
 [IDebugAsyncOperationCallBack 介面](../winscript/reference/idebugasyncoperationcallback-interface.md)  
 提供狀態事件與 `IDebugAsyncOperation` 介面評估的進度相關。  
  
 [IEnumDebugExpressionContexts 介面](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
 列舉 `IDebugExpressionContexts` 物件的集合。  
  
 [IProvideExpressionContexts 介面](../winscript/reference/iprovideexpressioncontexts-interface.md)  
 提供列舉某一元件已知的運算式內容。  
  
 [IDebugFormatter 介面](../winscript/reference/idebugformatter-interface.md)  
 允許語言或 IDE 自訂在不同的值之間的轉換或 VARTYPE 型別和字串。  
  
 [IDebugStackFrameSnifferEx 介面](../winscript/reference/idebugstackframesnifferex-interface.md)  
 列舉 PDM 的邏輯堆疊框架。  
  
## 主機  
 主機:  
  
-   裝載語言引擎。  
  
-   提供物件模型 \(可編寫指令碼\) 的物件集。  
  
-   定義可偵錯資料及其內容的樹狀結構。  
  
-   組織指令碼將虛擬應用程式。  
  
 有兩種主機:  
  
-   一沉默寡言的主應用程式支援基礎 Active Scripting 介面。  它無法控制資料結構或組織;指令碼完全由這個提供給語言引擎。  
  
-   智慧型主機支援允許它定義文件樹狀結構、資料內容和語法標色的更大的介面集合。  有一組 Helper 介面，描述在下一個區段，可讓主應用程式是智慧型主機。  
  
### 智慧型主機 Helper 介面  
 `IDebugDocumentHelper` 方法提供主應用程式可以使用取得智慧地載入的優點，而不需處理最大複雜的大幅簡化的一組介面 \(和\) 的完整功能的介面。  
  
 不需要當然主機使用這些介面，。  不過使用這些介面來避免實作或使用一些更複雜的介面。  
  
 [IDebugDocumentHelper 介面](../winscript/reference/idebugdocumenthelper-interface.md)  
 實作由 PDM 和為許多介面的實作所需的智慧標籤的載入。  
  
 [IDebugDocumentHost 介面](../winscript/reference/idebugdocumenthost-interface.md)  
 實作 \(選擇性地\) 是由主機所公開主應用程式特定功能，例如語法標色，在偵錯工具。  
  
 如需詳細資訊，請參閱[實作智慧主機協助程式介面](../winscript/implementing-smart-host-helper-interfaces.md)。  
  
### 完整智慧型主機介面  
 下面是完全可設定的介面智慧型主機必須實作或使用，如果不使用 Helper 介面。  
  
 主機實作的介面:  
  
 [IDebugDocumentInfo 介面](../winscript/reference/idebugdocumentinfo-interface.md)  
 在文件提供資訊，不一定能夠具現化。  
  
 [IDebugDocumentProvider 介面](../winscript/reference/idebugdocumentprovider-interface.md)  
 為執行個體化資料視需要提供。  
  
 [IDebugDocument 介面](../winscript/reference/idebugdocument-interface.md)  
 所有的基底介面偵錯資料。  
  
 [IDebugDocumentText 介面](../winscript/reference/idebugdocumenttext-interface.md)  
 提供對偵錯資料的純文字版本。  
  
 [IDebugDocumentTextAuthor 介面](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 允許編輯偵錯資料的純文字版本。  
  
 [IDebugDocumentContext 介面](../winscript/reference/idebugdocumentcontext-interface.md)  
 提供文件的部分的抽象表示偵錯。  
  
 PDM 實作的介面表示主機:  
  
 [IDebugApplicationNode 介面](../winscript/reference/idebugapplicationnode-interface.md)  
 透過在專案樹狀結構內的內容擴充 `IDebugDocumentProvider` 介面的功能。  
  
## 偵錯工具 IDE  
 IDE 是與語言無關的偵錯 UI。  它提供:  
  
-   文件檢視器\/編輯器。  
  
-   中斷點管理。  
  
-   運算式評估和監看式視窗。  
  
-   瀏覽的堆疊框架。  
  
-   瀏覽物件\/的類別。  
  
-   瀏覽虛擬應用程式結構。  
  
 偵錯工具實作的介面:  
  
 [IApplicationDebugger 介面](../winscript/reference/iapplicationdebugger-interface.md)  
 偵錯工具 IDE 工作階段公開的主要介面。  
  
 [IApplicationDebuggerUI 介面](../winscript/reference/iapplicationdebuggerui-interface.md)  
 將外部元件對偵錯工具的使用者介面 \(UI\) \(UI\) 的更多控制。  
  
 [IDebugExpressionCallBack 介面](../winscript/reference/idebugexpressioncallback-interface.md)  
 提供 `IDebugExpression` 評估進度的狀態事件。  
  
 [IDebugDocumentTextEvents 介面](../winscript/reference/idebugdocumenttextevents-interface.md)  
 提供值給關聯的 Word 文件的事件變更。  
  
 [IDebugApplicationNodeEvents 介面](../winscript/reference/idebugapplicationnodeevents-interface.md)  
 提供 `IDebugApplicationNode` 介面的事件介面。  
  
### 電腦偵錯管理員  
 電腦偵錯管理員會維護和列舉現用虛擬應用程式名稱可在虛擬應用程式和偵錯工具之間的連結。  
  
 [IDebugSessionProvider 介面](../winscript/reference/idebugsessionprovider-interface.md)  
 建立執行中應用程式的偵錯工作階段。  
  
 [IMachineDebugManager 介面](../winscript/reference/imachinedebugmanager-interface.md)  
 對電腦的主要介面偵錯管理員。  
  
 [IMachineDebugManagerCookie 介面](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 類似於 `IMachineDebugManager` 介面，不過，這個介面支援偵錯 Cookie。  
  
 [IMachineDebugManagerEvents 介面](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 在電腦維護的執行中應用程式清單上的信號變更偵錯管理員。  
  
 [IEnumRemoteDebugApplications 介面](../winscript/reference/ienumremotedebugapplications-interface.md)  
 列舉電腦上執行應用程式。  
  
### 處理序偵錯管理員  
 PDM 執行下列動作:  
  
-   同步處理多個語言偵錯引擎。  
  
-   維護偵錯文件樹狀結構。  
  
-   合併堆疊框架。  
  
-   座標中斷點和逐步跨語言引擎。  
  
-   追蹤執行緒。  
  
-   維護非同步處理中的偵錯工具執行緒。  
  
-   與電腦通訊偵錯管理員和偵錯工具 IDE。  
  
 下列程序提供的介面偵錯管理員。  
  
 [IProcessDebugManager 介面](../winscript/reference/iprocessdebugmanager-interface.md)  
 要處理的主要介面偵錯管理員。  這個介面可以從流程，加入或移除虛擬應用程式。  
  
 [IRemoteDebugApplication 介面](../winscript/reference/iremotedebugapplication-interface.md)  
 表示執行中的應用程式。  
  
 [IDebugApplication 介面](../winscript/reference/idebugapplication-interface.md)  
 提供語言引擎與主機使用的公開非遠端偵錯方法。  
  
 [IRemoteDebugApplicationThread 介面](../winscript/reference/iremotedebugapplicationthread-interface.md)  
 表示執行緒在特定應用程式中。  
  
 [IDebugApplicationThread 介面](../winscript/reference/idebugapplicationthread-interface.md)  
 允許語言引擎和主執行緒同步處理和維護執行緒特定，偵錯狀態資訊。  
  
 [IEnumRemoteDebugApplicationThreads 介面](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
 列舉型別在應用程式的執行緒。  
  
 [IDebugThreadCall 介面](../winscript/reference/idebugthreadcall-interface.md)  
 分派封送處理呼叫。  
  
 [IDebugApplicationNode 介面](../winscript/reference/idebugapplicationnode-interface.md)  
 保留資料的一個位置在階層架構中。  
  
 [IEnumDebugApplicationNodes 介面](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
 列舉節點的子節點與應用程式。  
  
 [IEnumDebugStackFrames 介面](../winscript/reference/ienumdebugstackframes-interface.md)  
 列舉堆疊框架與執行緒對應，合併引擎。  
  
 [IDebugCookie 介面](../winscript/reference/idebugcookie-interface.md)  
 在指令碼偵錯工具可讓偵錯設定 Cookie。  
  
 [IDebugHelper 介面](../winscript/reference/idebughelper-interface.md)  
 以一個 Factory 做為物件瀏覽器和簡單的連接點指令碼引擎的。  
  
 [ISimpleConnectionPoint 介面](../winscript/reference/isimpleconnectionpoint-interface.md)  
 為描述和列舉特定連接點引發的事件提供簡單的方式，指令碼引擎的。  
  
## 請參閱  
 [動態指令碼偵錯工具的介面](../winscript/reference/active-script-debugger-interfaces.md)