---
title: "IDebugApplicationNode100 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode100 介面"
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# IDebugApplicationNode100 介面
`IDebugApplicationNode100` 介面 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)擴充的功能。  您可以呼叫 [IDebugApplicationNode 介面](../../winscript/reference/idebugapplicationnode-interface.md)之實作的 QueryInterface 取得此介面的執行個體。  
  
> [!IMPORTANT]
>  這個介面是由 PDM v10.0 實作和更大。  位於 activdbg100.h。  
  
## 方法  
 `IDebugApplicationNode100` 介面公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|取得由指定之篩選條件隱藏的文字文件。|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|判斷指定的檔案是否屬於其中一個節點的子節點。|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|設定在特定 [IDebugApplicationNodeEvents 介面](../../winscript/reference/idebugapplicationnodeevents-interface.md) 實作的篩選條件。  它允許指令碼偵錯工具會篩選掉編譯器產生的子應用程式節點，使 PDM 不再傳送事件，當節點建立或移除時。  根據預設，所有節點會傳送。|