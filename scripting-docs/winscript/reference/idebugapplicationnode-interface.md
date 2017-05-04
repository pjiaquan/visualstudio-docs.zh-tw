---
title: "IDebugApplicationNode 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationNode 介面"
ms.assetid: 30be3a97-8191-45ac-8706-3f7056c163d6
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugApplicationNode 介面
`IDebugApplicationNode` 介面會提供專案樹狀目錄中做為內容擴充 `IDebugDocumentProvider` 介面的功能。  
  
 除了繼承自 `IDebugDocumentProvider` 的方法之外，`IDebugApplicationNode` 介面還會公開下列方法。  
  
## 方法的 Vtable 順序。  
  
|方法|描述|  
|--------|--------|  
|[IDebugApplicationNode::EnumChildren](../../winscript/reference/idebugapplicationnode-enumchildren.md)|列舉這個應用程式的子節點。|  
|[IDebugApplicationNode::GetParent](../../winscript/reference/idebugapplicationnode-getparent.md)|傳回此應用程式節點的父節點。|  
|[IDebugApplicationNode::SetDocumentProvider](../../winscript/reference/idebugapplicationnode-setdocumentprovider.md)|設定這個應用程式的文件的提供者。|  
|[IDebugApplicationNode::Close](../../winscript/reference/idebugapplicationnode-close.md)|這會導致應用程式釋放所有的參考和輸入了非現用狀態。|  
|[IDebugApplicationNode::Attach](../../winscript/reference/idebugapplicationnode-attach.md)|將這個應用程式會為指定的專案樹狀結構。|  
|[IDebugApplicationNode::Detach](../../winscript/reference/idebugapplicationnode-detach.md)|從專案樹狀結構中移除這個應用程式節點。|