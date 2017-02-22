---
title: "核心介面 | Microsoft Docs"
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
  - "偵錯 [偵錯 SDK]，核心介面"
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# 核心介面
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

下列的介面是藉由擴充偵錯工具的核心介面[!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]。  
  
## 討論  
 這些介面主要用來建立偵錯引擎 \(DE\)。  它們會在這裡依照分類進行組織：  
  
-   [中斷點](#Breakpoints)  
  
-   [內容](#Contexts)  
  
-   [核心的伺服器](#CoreServer)  
  
-   [偵錯引擎](#DebugEngines)  
  
-   [文件](#Documents)  
  
-   [事件](#Events)  
  
-   [運算式](#Expressions)  
  
-   [記憶體](#Memory)  
  
-   [模組](#Modules)  
  
-   [連接埠](#Ports)  
  
-   [處理序](#Processes)  
  
-   [程式](#Programs)  
  
-   [屬性](#Properties)  
  
-   [堆疊框架](#StackFrames)  
  
-   [執行緒](#Threads)  
  
-   [型別視覺化檢視](#TypeVisualizers)  
  
 可實作介面的實體為：  
  
-   偵錯引擎 \(DE\)  
  
-   連接埠提供者 \(PS\)  
  
-   運算式評估工具 \(EE\)  
  
-   Visual Studio \(VS\)  
  
##  <a name="Breakpoints"></a> 中斷點  
 這些介面相關的實作和追蹤的中斷點。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|表示繫結至的記憶體位置的中斷點。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|繫結中斷點的記憶體位置時，由 DE 傳送。|  
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|表示中斷點要求的文件加總檢查碼。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|中斷點無法繫結到的記憶體位置時，由 DE 傳送。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|當到達中斷點時，由 DE 傳送。|  
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|表示要求的中斷點。 用於建立暫止中斷點。|  
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|表示要求的中斷點。 用於建立暫止中斷點。|  
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|表示用來繫結中斷點的資訊。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|從記憶體位置中斷點是未繫結時，所 DE 傳送。|  
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|代表無效的中斷點 \(所傳回的`IDebugBreakpointErrorEvent2`\)。|  
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|表示解析度資訊不正確的中斷點。|  
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|表示函式中設有中斷點的位置。|  
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|表示中斷點要繫結。 用於建立繫結的中斷點。|  
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|表示資料集的繫結中斷點的列舉型別。|  
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|代表針對不會繫結至的記憶體位置的中斷點的集合的列舉型別。|  
  
##  <a name="Contexts"></a> 內容  
 這些介面代表不同的內偵錯程式的內容。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|代表程式碼指示的起始位置。|  
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|延伸[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)介面，可讓模組和程序的介面的擷取。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS DE|代表文件中的位置。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示用來評估運算式的內容。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|代表在一系列位元組的記憶體中的起始位置。|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|表示在中斷點或例外狀況的堆疊框架內容。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|表示在中斷點或例外狀況的堆疊框架內容。|  
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|表示列舉型別資料集的程式碼內容中。|  
  
##  <a name="CoreServer"></a> 核心的伺服器  
 這些介面代表的電腦正在進行偵錯程式。  這些由實作[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ，但可以被呼叫，將偵錯引擎。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|提供存取連接埠和通訊埠供應商，以及電腦的相關資訊。|  
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|表示[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)支援遠端偵錯。|  
  
##  <a name="DebugEngines"></a> 偵錯引擎  
 這些介面代表偵錯引擎和其相關聯的事件。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|代表自訂的偵錯引擎。|  
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|表示支援載入符號、 JustMyCode 和例外狀況的自訂的偵錯引擎。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|每個 DE 的新執行個體傳送到代表它已準備好處理偵錯工作。|  
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|表示支援程式的啟動自訂的偵錯引擎。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE PS|代表會處理多個偵錯引擎的程式節點。|  
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|提供方法讓偵錯引擎取得介面執行緒、 程式或堆疊框架 SDM。|  
  
##  <a name="Documents"></a> 文件  
 這些介面代表文件 \(原始程式檔\) 和其相關聯的項目。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|DE 傳送以要求要開啟的文件。|  
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|表示從文件的反組譯指令資料流。|  
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS DE|表示 DE，指定一個名稱和類別 ID \(CLSID\) 所提供的文件。|  
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE EE|代表總和檢查碼的偵錯的文件，可讓元件之間傳遞的加總檢查碼。|  
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS DE|代表文件內容，相對於特定的陳述式和程式碼內容的文件中的位置。|  
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS DE|代表文件中的一般位置。|  
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|代表原始程式檔中的字元位移的位置。|  
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS DE|表示文字文件 DE 所提供的 \(衍生自[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\)，提供實際的文字。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|若要指定在記憶體中的原始程式檔的變更傳送 DE。|  
  
##  <a name="Events"></a> 事件  
 這些介面代表 DE 」 和 「 工作階段偵錯管理員 」 \(SDM\) 之間傳送的所有事件。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|DE 傳送以要求要開啟的文件。|  
|[IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md)|DE|偵錯引擎 \(DE\) 這個介面過程中傳送至工作階段偵錯管理員 \(SDM\) 設定的狀態訊息列符號載入。|  
|[IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)|DE|在完成程式的分頁線時，由 DE 傳送。|  
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|繫結中斷點時，由 DE 傳送。|  
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|中斷點無法繫結時，由 DE 傳送。|  
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|當到達中斷點時，由 DE 傳送。|  
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|中斷點是未繫結時，所 DE 傳送。|  
|[IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)|DE|傳送 DE 以判斷是否應該停止在特定的位置。|  
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|若要指定在記憶體中的原始程式檔的變更傳送 DE。|  
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|每個 DE 的新執行個體傳送到代表它已準備好處理偵錯工作。|  
|[IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)|DE|傳送 DE 來表示所偵錯程式已經準備好執行第一個指令。|  
|[IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)|DE|其他的事件介面，可能會傳回錯誤，用來提供人們可讀取的錯誤訊息的介面。|  
|[IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)|DE PS|介面都衍生自其他所有事件的基底介面。|  
|[IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)|VS|表示事件 \(以實作特定的事件介面的物件表示\) 會傳送 SDM 所實作的介面。|  
|[IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)|DE|在偵錯程式中發生例外狀況時，所 DE 傳送。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|完成非同步運算式評估時，由 DE 傳送。|  
|IDebugFindSymbolEvent2||已過時。  請勿使用。|  
|[IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md)|DE|被攔截的例外狀況的處理完成後，由 DE 傳送。|  
|[IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)|DE|程式已經完成載入時傳送 DE。|  
|[IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)|DE|傳送將 IDE 顯示 DE 告知性訊息給使用者。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|當您載入或卸載模組時，由 DE 傳送。|  
|[IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md)|DE|訊號[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]偵錯工具使用者介面來警告使用者符號找不到被啟動的可執行檔。|  
|[IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)|DE|傳送將 IDE 顯示 DE 的任意字串。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|VS DE|連接埠傳送至任何接聽程式通訊連接埠的事件。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE PS|在建立處理程序之後，請傳送 DE 或連接埠。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE PS|當處理程序已被終結時傳送 DE 或連接埠。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE PS|在建立程式之後，請傳送 DE 或連接埠。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE PS|程式已被終結時傳送 DE 或連接埠。|  
|[IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md)|DE|啟用偵錯引擎來覆寫預設行為的[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI，當您結束偵錯工作階段。|  
|[IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md)|DE|程式的名稱變更時傳送從偵錯引擎 \(DE\) 工作階段偵錯管理員 \(SDM\)。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|傳送的是，當新的屬性 \(由`IDebugProperty2`介面\) 已建立。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|屬性已被終結時，所 DE 傳送。|  
|[IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md)|DE|傳送 DE 當逐步用盡或進入函式，所以會正確地顯示傳回的值。|  
|[IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)|VS|啟用偵錯引擎讀取公制設定遠端。|  
|[IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md)|DE|插入、 多於還是超出指令的步驟完成後，由 DE 傳送。|  
|[IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)|DE|傳送 DE 以指示成功或失敗的載入模組的符號。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|在建立執行緒之後，由 DE 傳送。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|在終結執行緒時，所 DE 傳送。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|執行緒已變更它的名稱時，所 DE 傳送。|  
  
##  <a name="Expressions"></a> 運算式  
 這些介面代表特定內文中將被評估的運算式。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|表示要評估的運算式。  取自[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)介面。|  
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|表示用來評估運算式的內容。  取自[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)介面。|  
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|完成非同步運算式評估時，由 DE 傳送。|  
  
##  <a name="Memory"></a> 記憶體  
 這些介面代表記憶體中的位元組序列。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|表示可讀取或寫入的記憶體中的位元組序列。|  
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|表示位元組序列的記憶體的位置。|  
  
##  <a name="Modules"></a> 模組  
 這些介面代表相對於可執行檔的模組或。DLL 檔案。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|代表單一的可執行檔或 DLL。|  
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|表示[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) ，支援符號。|  
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|當您載入或卸載模組時，由 DE 傳送。|  
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|表示包含在 PDB 檔的來源伺服器資訊。|  
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|表示列舉型別資料集未知的模組的[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)。|  
  
##  <a name="Ports"></a> 連接埠  
 這些介面代表連接埠和通訊埠供應商。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)|VS PS|代表本機電腦上的預設連接埠。|  
|[IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)|VS|啟用偵錯引擎使用 DCOM 來問[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ，確定防火牆會封鎖遠端偵錯的 UI。|  
|[IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)|VS PS|表示連接埠。|  
|[IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md)|PS|連接埠傳送至任何接聽程式通訊連接埠的事件。|  
|[IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)|PS|代表一個連接埠，可以啟動並終止處理序。|  
|[IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md)|PS|用來註冊和取消註冊程式與連接埠。 允許的通訊埠，來追蹤目前正在進行偵錯的程式。|  
|[IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)|PS|代表自訂使用者介面選取 \[連接埠。|  
|[IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)|VS|表示連接埠的新的連接埠會建立或找到的要求。|  
|[IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)|PS|表示 \[供應商的連接埠。|  
|[IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)|PS|表示可以保存的連接埠的供應商 \(儲存至磁碟\) 它所建立的連接埠的相關資訊。|  
|[IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md)|PS|可讓[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] UI，以顯示內部文字**傳輸資訊**一節的**附加至處理序**對話方塊。|  
|[IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md)|VS|可讓查詢目標電腦的相關資訊。|  
|[IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)|VS PS|表示一組連接埠上的列舉型別。|  
|[IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)|VS|代表在一組連接埠的供應商的列舉型別。|  
  
##  <a name="Processes"></a> 處理序  
 這些介面代表單一的可執行檔包含一或多個程式處理程序。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS，DE|代表正在電腦上執行的處理序。|  
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS，DE|代表正在支援的處理序偵錯 \(用來取代步驟，繼續，並在執行方法[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)介面\)。|  
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE PS|在建立處理程序之後，請傳送 DE 或連接埠。|  
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE PS|當處理程序已被終結時傳送 DE 或連接埠。|  
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|表示必須追蹤哪一個工作階段附加至它的處理程序。|  
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|表示一組連接埠上的處理序的列舉型別。|  
  
##  <a name="Programs"></a> 程式  
 這些介面代表執行的這不一定對應到實體的可執行檔或模組的邏輯單位的程式。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|表示[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ，以便與其他同時進行偵錯的程式正常運作。|  
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE PS|代表一個邏輯單位的執行。|  
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE PS|在建立程式之後，請傳送 DE 或連接埠。|  
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE PS|程式已被終結時傳送 DE 或連接埠。|  
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE PS|表示[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) ，可以由多個偵錯引擎。|  
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|表示[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ，必須能夠追蹤哪一個工作階段附加至它。|  
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE PS|表示[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) ，可能會傳回執行中的程序的相關資訊。|  
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE PS|代表一種程式，才能進行偵錯。|  
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE PS|允許嘗試附加至相關聯的程式，接受通知的程式\] 節點。|  
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|提供方法來查詢有關受該 DE 程式將 DE SDM。|  
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|若要用來顯示它們正在進行偵錯 SDM 登錄程式使用 DEs。|  
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE PS|表示[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) ，可以跨執行緒或處理序界限封送介面。|  
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE PS|表示一組程式的列舉型別。|  
  
##  <a name="Properties"></a> 屬性  
 這些介面代表特定內容，通常的運算式評估結果相關聯的值的屬性。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|表示[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) ，可以用自訂的方式來顯示它的值。|  
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|表示堆疊框架、 文件，或運算式評估的結果值。|  
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|表示[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)支援任意長度的字串。|  
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|傳送的是，當新的屬性 \(由[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)介面\) 已建立。|  
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|屬性已被終結時，所 DE 傳送。|  
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|表示參考的屬性，可存在於任何特定的堆疊框架外緣。|  
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|表示列舉型別資料集的[DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)結構而描述變數、 暫存器、 參數和運算式。|  
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|表示列舉型別資料集的[DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)結構。|  
  
##  <a name="StackFrames"></a> 堆疊框架  
 這些介面代表一個堆疊框架的內容中的中斷點或例外狀況發生。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|表示內容中的中斷點或例外狀況發生。|  
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|表示[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)而可以處理攔截例外狀況。|  
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|表示列舉型別資料集的[CODE\_PATH](../../../extensibility/debugger/reference/code-path.md)結構而指定函式呼叫用來在特定的堆疊框架分時抵達的順序。|  
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|表示列舉型別資料集的[FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)結構描述堆疊框架。|  
  
##  <a name="Threads"></a> 執行緒  
 這些介面代表執行緒和其相關聯的事件。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|代表執行的執行緒。|  
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|在建立執行緒之後，由 DE 傳送。|  
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|在終結執行緒時，所 DE 傳送。|  
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|執行緒已變更它的名稱時，所 DE 傳送。|  
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|表示列舉型別，透過一組執行緒。|  
  
##  <a name="TypeVisualizers"></a> 型別視覺化檢視  
 這些介面會提供型別視覺化檢視中的支援。  這些介面通常是由運算式評估工具的方式實作。  
  
|介面|藉由實作|描述|  
|--------|----------|--------|  
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|代表要向型別視覺化檢視的位元組陣列。|  
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|提供可用來取得要傳遞至型別視覺化檢視的資料存取的方法。|  
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|表示屬性，可存取[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)的實作。|  
  
## 請參閱  
 [應用程式開發介面參考](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)   
 [建立自訂的偵錯引擎](../../../extensibility/debugger/creating-a-custom-debug-engine.md)