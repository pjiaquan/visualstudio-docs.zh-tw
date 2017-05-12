---
title: "IProcessDebugManager 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IProcessDebugManager 介面"
ms.assetid: b6ecb2bd-a4d1-4857-9232-036c154d0cb1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProcessDebugManager 介面
要處理的主要介面偵錯處理常式。  這個介面可以從處理序中建立，加入或移除虛擬應用程式。  它可以列舉堆疊框架和應用程式執行緒。  
  
 除了繼承自 `IUnknown` 的方法之外，`IProcessDebugManager` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IProcessDebugManager::CreateApplication](../../winscript/reference/iprocessdebugmanager-createapplication.md)|建立新的偵錯該應用程式的應用程式物件。|  
|[IProcessDebugManager::GetDefaultApplication](../../winscript/reference/iprocessdebugmanager-getdefaultapplication.md)|傳回目前處理序的預設應用程式物件。|  
|[IProcessDebugManager::AddApplication](../../winscript/reference/iprocessdebugmanager-addapplication.md)|將應用程式加入至電腦進行偵錯執行中應用程式管理器的清單。|  
|[IProcessDebugManager::RemoveApplication](../../winscript/reference/iprocessdebugmanager-removeapplication.md)|執行應用程式的清單中移除應用程式。|  
|[IProcessDebugManager::CreateDebugDocumentHelper](../../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)|建立新的偵錯該應用程式的文件 Helper。|