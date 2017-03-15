---
title: "如何: 新增標準文字標記 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "編輯器 [Visual Studio SDK]，舊版的標準文字標記"
ms.assetid: a39fca69-0014-474c-933f-51f0e9b9617e
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# 如何: 新增標準文字標記
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

若要建立一個具有所提供的預設文字標記型別使用下列程序[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]核心編輯器。  
  
### 若要建立文字標記  
  
1.  根據您所使用的一或兩位二維座標系統，請打<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A>方法或<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream.CreateStreamMarker%2A>方法，以建立新的文字標記。  
  
     在這個方法呼叫中，指定標記型別，以透過，建立資料標記的文字範圍和<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面。  然後，這個方法會傳回一個指標至新建立的文字標記。  標記型別取自<xref:Microsoft.VisualStudio.TextManager.Interop.MARKERTYPE>列舉型別。  指定<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>介面如果您想要的標記事件通知。  
  
    > [!NOTE]
    >  只有主要 UI 執行緒上建立文字標記。  核心編輯器是要建立文字的標記文字緩衝區的內容，而文字緩衝區中並不具備執行緒安全。  
  
## 新增自訂命令  
 實作`IVsTextMarkerClient`介面，並提供給它的指標，從標記增強了幾種方式標記行為。  首先，這可讓您提供您的資料標記的秘訣，並執行命令。  這也可讓您接收事件通知的個別資料標記，並建立自訂快顯功能表上的標記。  將自訂命令新增至標記快顯功能表，請使用下列程序。  
  
#### 若要將自訂命令新增到快顯功能表  
  
1.  環境呼叫的快顯功能表會顯示之前， <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.GetMarkerCommandInfo%2A>方法和您的文字標記是指向受影響的階段，以及快顯功能表中的 \[指令\] 項目的數目。  
  
     例如，快顯功能表上的中斷點專屬命令包括**移除中斷點** 到 **新增中斷點**，如下列螢幕擷取畫面所示。  
  
     ![標記內容功能表](../extensibility/media/vsmarkercontextmenu.png "vsMarkercontextmenu")  
  
2.  傳遞回用來識別自訂指令名稱的一些文字。  例如， **移除中斷點**可能是自訂的指令，如果環境是否已提供參數。  您也傳回來的命令是否支援、 可用且處於啟用狀態，及 \(或\) 在捨去切換。  環境會使用這項資訊，在快顯功能表中的 \[自訂\] 指令顯示正確的方式。  
  
3.  若要執行命令時，環境呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient.ExecMarkerCommand%2A>方法，傳遞文字標記，並從內容功能表選取命令的數目的指標。  
  
     使用這項資訊從這個呼叫來執行任何動作的文字標記您的自訂命令規定。  
  
## 請參閱  
 [使用舊版 API 中的文字標記](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [How to: 實作錯誤標記](../extensibility/how-to-implement-error-markers.md)   
 [如何: 建立自訂文字標記](../extensibility/how-to-create-custom-text-markers.md)   
 [如何: 使用文字標記](../extensibility/how-to-use-text-markers.md)