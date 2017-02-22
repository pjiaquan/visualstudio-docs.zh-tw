---
title: "使用舊版 API 存取 Text 檢視 | Microsoft Docs"
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
  - "編輯器 [Visual Studio SDK]，傳統的文字檢視"
ms.assetid: 8f751f72-c972-4be3-84ee-19c281e02e25
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# 使用舊版 API 存取 Text 檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文字檢視是儲存在文字緩衝區中的文字呈現。  您可以使用舊版 API 下, 一節中所示，以存取文字檢視。  
  
## 文字檢視物件  
 每一個檢視表已經有它自己的文字緩衝區，而檢視是在緩衝區中資料的視窗。  下圖顯示的索引鍵的介面由文字檢視物件的<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView>。  
  
 ![Visual Studio 文字檢視物件](../extensibility/media/vstextview.png "vstextview")  
文字檢視物件  
  
 檢視是一種呈現文字緩衝區中。  使您在檢視中所看到的內容都不確切的緩衝區中的文字，其中包括文字換行功能，以及製作大綱，等功能。  
  
 檢視可讓其他服務或攔截連入的命令和回應它們之前檢視在其上所做的處理程序。  若要這麼做最常見的服務是語言服務。  語言服務可能需要，比方說，攔截 ENTER 鍵，以提供自訂的縮排的行為或工具提示的指令。  
  
## 將功能加入到文字檢視  
 您可以自訂文字檢視行為，藉由處理特定的按鍵動作。  在您實作攔截按鍵動作， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>上您的物件，並提供命令目標 \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>\) 監視器及截距命令。  
  
 文字檢視命令的篩選器會使用循序的架構。  新命令的篩選器 \(<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>物件\) 會加入至序列，藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>方法。  
  
 文字檢視的事件通知由使用`T:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents`介面。  在您接收到文字檢視的變更通知的用戶端物件上實作這個介面。  公開到文字檢視這個介面，方法是使用<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>上的文字檢視，以從檢視中接收變更通知的介面。  
  
## 請參閱  
 [使用舊版 API 來變更檢視設定](../extensibility/changing-view-settings-by-using-the-legacy-api.md)   
 [使用文字管理員監控全域設定](../extensibility/using-the-text-manager-to-monitor-global-settings.md)