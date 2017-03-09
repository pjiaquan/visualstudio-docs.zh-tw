---
title: "VsgDbg 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6722263c-ccef-40c7-a0ae-87a863fbab00
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg 類別
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

表示圖形診斷應用程式元件的程式設計控制項的介面。  
  
## 語法  
  
```cpp  
class VsgDbg;  
```  
  
## Members  
 `VsgDbg` 類別支援下列成員：  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[VsgDbg::VsgDbg \(建構函式\)](../Topic/VsgDbg::VsgDbg%20\(Constructor\).md)|建構 `VsgDbg` 類別的執行個體，並選擇性準備圖形診斷應用程式元件，以有效地擷取和記錄圖形資訊。|  
|[VsgDbg::~VsgDbg \(解構函式\)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)|移除 `VsgDbg` 類別的執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[AddMessage](../debugger/addmessage.md)|將自訂訊息加到圖形診斷 HUD \(Head\-Up Display\)。|  
|[BeginCapture](../debugger/begincapture.md)|以擷取間隔的開頭，會由 `EndCapture` 結束。|  
|[CaptureCurrentFrame](../debugger/capturecurrentframe.md)|擷取目前框架的其餘部分至圖形記錄檔。|  
|[複製 \(程式設計擷取\)](../debugger/copy-programmatic-capture.md)|將作用中的圖形記錄 \(.vsglog\) 內容複複製到新檔案內。|  
|[EndCapture](../debugger/endcapture.md)|結束從`BeginCapture`開始的擷取間隔。|  
|[Init](../debugger/init.md)|準備圖形診斷應用程式元件，以有效地擷取並記錄圖形資訊。|  
|[ToggleHUD](../debugger/togglehud.md)|切換圖形診斷 HUD 覆疊的開關。|  
|[UnInit](../debugger/uninit.md)|完成圖形記錄檔並關閉，在應用程式有效地記錄圖形資訊後，釋放使用的資源。|  
  
## 備註  
 `VsgDbg` 類別表示可用於以程序方式，控制圖形診斷功能的介面。  當您無法有效地擷取和記錄圖形資訊時，可以使用這些功能：`AddMessage` 成員函式和 `ToggleHUD` 成員函式。  其他成員函式會準備圖形診斷應用程式元件，以啟動或停止作用中的擷取圖形資訊擷取，或者在應用程式擷取和記錄圖形資訊至圖形記錄檔時被呼叫。