---
title: "如何: 使用文字標記 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版-使用文字標記"
ms.assetid: 76eed51c-eecb-4579-823e-13df2f0526b9
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 如何: 使用文字標記
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

文字標記可以套用至編輯<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer>物件。  
  
## 程序  
  
#### 若要套用文字資料標記  
  
1.  取得執行個體的<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager>類別。  
  
    > [!NOTE]
    >  核心編輯器會自動套用標準的文字標記編輯它，所有文件，並應不需明確地套用標準的文字標記。  
  
2.  取得您有興趣點撥打標記的標記型別 ID <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>方法以`GUID`文字標記您想要使用。  
  
    > [!NOTE]
    >  請勿使用`GUID` VSPackage 或提供文字標記的服務。  
  
3.  使用資料標記的型別 ID 可以藉由呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManager.GetRegisteredMarkerTypeID%2A>方法當做參數來呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>方法，以套用至指定的文字區域的文字標記。  
  
#### 若要將功能加入至文字資料標記  
  
1.  它可能不需要額外的功能加入文字標記，例如工具提示、 特殊的快顯功能表或處理常式的特殊情況。  若要執行這項操作：  
  
2.  建立物件的實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面。  
  
3.  如果需要額外的功能，來實作<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>，以及<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>上相同的物件實作的介面<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面。  
  
4.  傳遞<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面，建立對呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>用來將文字標記套用至指定的文字區域的方法。  
  
5.  文字標記區域中加入內容功能表支援時，不必建立功能表。  
  
     如需有關如何建立內容功能表，請參閱[內容功能表](../extensibility/context-menus.md)。  
  
6.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]環境呼叫的方法所提供的介面，例如<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetTipText%2A>方法，或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>所需的方法。  
  
## 請參閱  
 [使用舊版 API 中的文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [如何: 新增標準文字標記](../extensibility/how-to-add-standard-text-markers.md)   
 [如何: 建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)   
 [How to: 實作錯誤標記](../extensibility/how-to-implement-error-markers.md)