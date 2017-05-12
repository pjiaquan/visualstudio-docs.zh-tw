---
title: "IEnumRemoteDebugApplications 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IEnumRemoteDebugApplications 介面"
ms.assetid: ceb5fbe7-d131-4352-9dd1-af80acd3f3f7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumRemoteDebugApplications 介面
列舉型別 \(Enumeration\) 應用程式物件。  這個介面可用來「至應用程式的附加」對話方塊用來列舉電腦上執行的應用程式。  
  
 除了繼承自 `IUnknown` 的方法之外，`IEnumRemoteDebugApplications` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IEnumRemoteDebugApplications::Clone](../../winscript/reference/ienumremotedebugapplications-clone.md)|建立列舉程式，其中包含與目前列舉程式相同的狀態。|  
|[IEnumRemoteDebugApplications::Next](../../winscript/reference/ienumremotedebugapplications-next.md)|擷取區段的指定數目在列舉型別序列中|  
|[IEnumRemoteDebugApplications::Reset](../../winscript/reference/ienumremotedebugapplications-reset.md)|將列舉序列重設到開頭。|  
|[IEnumRemoteDebugApplications::Skip](../../winscript/reference/ienumremotedebugapplications-skip.md)|略過區段的指定數目在列舉型別序列中|