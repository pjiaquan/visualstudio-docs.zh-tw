---
title: "IDebugDocumentHost 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentHost 介面"
ms.assetid: 2fed4220-b6a2-47c6-bf28-daad7dd5c42d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentHost 介面
公開主應用程式特定功能，例如語法配色，在偵錯工具。  `IDebugDocumentHelper::SetDebugDocumentHost` 方法採用此介面做為引數。  
  
 除了繼承自 `IUnknown` 的方法之外，`IDebugDocumentHost` 介面還會公開下列方法。  
  
## 依照 Vtable 順序的方法  
  
|方法|描述|  
|--------|--------|  
|[IDebugDocumentHost::GetDeferredText](../../winscript/reference/idebugdocumenthost-getdeferredtext.md)|您可以使用 `IDebugDocumentHelper::AddDeferredText`，傳回加入字元範圍，原始主應用程式文件。|  
|[IDebugDocumentHost::GetScriptTextAttributes](../../winscript/reference/idebugdocumenthost-getscripttextattributes.md)|傳回文件文字區塊的文字屬性變更為。|  
|[IDebugDocumentHost::OnCreateDocumentContext](../../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)|告知主應用程式建立新的資料內容，並建立可讓主應用程式會選擇性地傳回物件控制新內容。|  
|[IDebugDocumentHost::GetPathName](../../winscript/reference/idebugdocumenthost-getpathname.md)|傳回完整路徑 \(包括檔案名稱\) 文件來源檔案。|  
|[IDebugDocumentHost::GetFileName](../../winscript/reference/idebugdocumenthost-getfilename.md)|傳回文件的名稱，但不包含路徑，資訊。|  
|[IDebugDocumentHost::NotifyChanged](../../winscript/reference/idebugdocumenthost-notifychanged.md)|告知主應用程式文件來源檔案未儲存，並重新整理其內容。|