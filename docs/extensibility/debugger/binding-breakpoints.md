---
title: "繫結中斷點 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "繫結的中斷點"
ms.assetid: 70737387-c52f-4dae-8865-77d4b203bf25
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# 繫結中斷點
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

如果使用者設定中斷點，可能是藉由按下 f9 鍵，IDE 」 主要是要求並提示偵錯工作階段，若要建立中斷點。  
  
## 設定中斷點  
 設定中斷點所以兩個步驟，程式碼或資料中斷點會受到可能還無法使用。  首先，必須說明中斷點，然後，程式碼或資料可用時，它必須繫結到該程式碼或資料，如下所示：  
  
1.  中斷點不請求從相關的偵錯引擎 \(DEs\)，並且再中斷點已結合的程式碼或資料可供使用。  
  
2.  中斷點要求傳送至偵錯工作階段，將其傳送至所有相關的 DEs。  選擇要處理中斷點任何 DE 建立對應的暫止中斷點。  
  
3.  偵錯工作階段收集的暫止中斷點，並將它們傳送回偵錯套件 \(Visual Studio 的偵錯元件\)。  
  
4.  偵錯封裝會提示您偵錯工作階段，以將暫止中斷點的程式碼或資料繫結。  偵錯工作階段會將這個要求傳送到所有相關的 DEs。  
  
5.  如果是可繫結中斷點，它會傳送中斷點繫結到偵錯工作階段的事件。  如果沒有出現，而是傳送中斷點錯誤事件。  
  
## 暫止中斷點  
 暫止中斷點可以繫結到多個程式碼的位置。  例如，c \+ \+ 樣板的來源程式碼的行可以繫結至每個範本所產生的程式碼順序。  偵錯工作階段可以使用中斷點繫結之事件，來列舉傳送事件的時間在繫結中斷點的程式碼內容。  更新版本中，可以繫結多個程式碼內容，因此 DE 可能會傳送多個中斷點繫結的每個繫結要求的事件。  不過，將 DE 應該傳送一個中斷點錯誤事件，每個繫結要求。  
  
## 實作  
 偵錯封裝呼叫工作階段偵錯管理員 \(SDM\) 並讓它只能以程式設計的方式， [IDebugBreakpointRequest2](../../extensibility/debugger/reference/idebugbreakpointrequest2.md)介面包裝[BP\_REQUEST\_INFO](../../extensibility/debugger/reference/bp-request-info.md)結構描述設定中斷點。  中斷點可以有許多種形式，雖然它們最終會解析至程式碼或資料內容。  
  
 SDM 藉由呼叫傳遞至每個相關的 DE 這個呼叫其[CreatePendingBreakpoint](../../extensibility/debugger/reference/idebugengine2-creatependingbreakpoint.md)方法。  如果 DE 選擇處理中斷點，它會建立並傳回[IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)介面。  SDM 會收集這些介面，並將它們傳送至偵錯封裝成單一`IDebugPendingBreakpoint2`介面。  
  
 到目前為止，已不產生任何事件。  
  
 偵錯套件再嘗試將暫止中斷點的程式碼或資料繫結藉由呼叫[繫結](../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)，這由 DE 實作。  
  
 如果中斷點繫結時，便會傳送 DE [IDebugBreakpointBoundEvent2](../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)事件介面到偵錯的封裝。  藉由呼叫這個介面以列舉所有的程式碼內容 \(或單一的資料內容\) 繫結至中斷點的偵錯套件使用[EnumBoundBreakpoints](../../extensibility/debugger/reference/idebugbreakpointboundevent2-enumboundbreakpoints.md)，至少有一個傳回的[IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)介面。  [GetBreakpointResolution](../../extensibility/debugger/reference/idebugboundbreakpoint2-getbreakpointresolution.md)介面傳回[IDebugBreakpointResolution2](../../extensibility/debugger/reference/idebugbreakpointresolution2.md)介面，以及[GetResolutionInfo](../../extensibility/debugger/reference/idebugbreakpointresolution2-getresolutioninfo.md)會傳回[BP\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-resolution-info.md)等位包含程式碼或資料內容。  
  
 如果 DE 無法繫結中斷點時，它會傳送一個[IDebugBreakpointErrorEvent2](../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)事件介面到偵錯的封裝。  偵錯封裝擷取錯誤類型 \(錯誤或警告\) 和資訊訊息藉由呼叫[GetErrorBreakpoint](../../extensibility/debugger/reference/idebugbreakpointerrorevent2-geterrorbreakpoint.md)，後面緊接著[GetBreakpointResolution](../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md)和[GetResolutionInfo](../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)。  這會傳回[BP\_ERROR\_RESOLUTION\_INFO](../../extensibility/debugger/reference/bp-error-resolution-info.md)結構，包含錯誤類型和訊息。  
  
 如果將 DE 處理中斷點，但無法將它繫結，則會傳回型別的錯誤`BPET_TYPE_ERROR`。  偵錯封裝回應方式顯示錯誤對話方塊，並將 IDE 放在左邊的原始程式碼行的中斷點圖像的驚嘆號圖像 \(glyph\)。  
  
 如果將 DE 處理中斷點、 無法繫結，但其他 DE 可能會將其繫結，則它會傳回一則警告。  IDE 會做為回應放置在左邊的原始程式碼行的中斷點圖像的問題圖像 \(glyph\)。  
  
## 請參閱  
 [偵錯工作](../../extensibility/debugger/debugging-tasks.md)