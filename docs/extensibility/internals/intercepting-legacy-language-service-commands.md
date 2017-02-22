---
title: "攔截舊版語言服務命令 | Microsoft Docs"
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
  - "攔截語言服務的命令"
  - "語言服務，攔截命令"
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 攔截舊版語言服務命令
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

與[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]，您可以讓文字檢視會處理的語言服務攔截命令。  這是適用於特定語言的文字檢視未管理的行為。  您可以將一或多個命令的篩選器新增到文字檢視中，從您的語言服務攔截這些命令。  
  
## 取得和路由命令  
 指令篩選條件是<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>會監視特定的字元順序或鍵命令的物件。  如果省略檢視時，可以使一個以上的命令過濾器。  每個文字檢視會維護鏈結的命令的篩選器。  建立新的 「 指令 」 篩選器之後，您會將篩選新增至適當的文字檢視的鏈結中。  
  
 呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>上的方法<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>加入鏈結中的命令篩選。  當您呼叫<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>， [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]傳回另一個命令過濾器可以傳遞命令篩選程式無法處理的指令。  
  
 您有命令處理的下列選項：  
  
-   處理命令，然後將傳遞至下一個命令過濾器命令鏈結中。  
  
-   處理命令，以及傳送下一個命令過濾器上的命令。  
  
-   無法處理命令，但傳遞至下一個命令過濾器命令。  
  
-   略過的指令。  無法處理它在目前的篩選條件，並依序執行不傳遞到下一個篩選常式。  
  
 語言服務應該處理哪一個指令的相關資訊，請參閱[語言服務篩選器的重要命令](../../extensibility/internals/important-commands-for-language-service-filters.md)。