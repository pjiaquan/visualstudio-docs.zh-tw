---
title: "IDebugDocumentProvider 介面 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentProvider 介面"
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugDocumentProvider 介面
為執行個體化資料提供資料倉儲。  
  
## 備註  
 這種間接方式為執行個體化資料:  
  
-   會在需要時，只允許載入文件。  
  
-   允許文件物件在偵錯工具 IDE 內。  
  
-   允許多個模式存取相同的資料物件。  
  
 這會從其提供者有效地分隔文件並允許提供者帶有其他執行階段，內容資訊。  
  
 除了繼承自 `IDebugDocumentInfo` 的方法之外，`IDebugDocumentProvider` 介面還會公開下列方法。  
  
|方法|描述|  
|--------|--------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|如果檔案不存在，讓文件具現化。|