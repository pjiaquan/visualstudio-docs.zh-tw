---
title: "使用文字管理員監控全域設定 | Microsoft Docs"
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
  - "編輯器 [Visual Studio SDK]，舊版的監視全域設定"
  - "編輯器 [Visual Studio SDK]，舊版-文字管理員"
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用文字管理員監控全域設定
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

如果您決定核心編輯器使用，您必須監視全域設定，所做的變更，因為這些變更可能會影響您的編輯器\] 中的執行個體。  您可以聆聽文字管理員所引發的事件，以追蹤所做的變更。  比方說，當您在核心編輯器，例如其文件的資料物件，指定通用偏好使用的外觀或行為，元件的文字管理員儲存這項資訊和通訊其所有受影響的用戶端。  
  
## 文字管理員函式  
 文字管理員會引發事件的設定，包括下列：  
  
-   緩衝區是否在原始檔控制之下  
  
-   如何註冊檔案變更通知  
  
-   為了持續追蹤哪些檢視會以特定的緩衝區關聯的方式  
  
-   文字顏色標示喜好設定  
  
-   與空間喜好設定\] 索引標籤  
  
 文字管理員無法管理對指定的語言都是唯一的喜好設定。  這些設定必須管理每個語言服務。  
  
 文字管理員的事件通知由<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents>介面。  實作這個介面上您的用戶端物件來處理事件引發文字管理員。  使用註冊這些事件<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>上文字管理員介面。  
  
## 請參閱  
 [核心編輯器內](../extensibility/inside-the-core-editor.md)   
 [Editor Features](http://msdn.microsoft.com/zh-tw/bdac940d-1f14-4019-a01f-fd0bb3dc7198)