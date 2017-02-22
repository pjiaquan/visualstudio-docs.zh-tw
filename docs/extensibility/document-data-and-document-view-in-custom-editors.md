---
title: "文件資料，以及在自訂編輯器中的文件檢視 | Microsoft Docs"
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
  - "編輯器 [Visual Studio SDK]，自訂的文件資料，以及文件檢視"
ms.assetid: 71eea623-f566-4feb-84cd-ca1ba71bc493
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# 文件資料，以及在自訂編輯器中的文件檢視
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

自訂編輯器包含兩個部分 ︰ 文件資料物件和文件的檢視物件。 如名稱所示，文件資料物件代表要顯示的文字資料，而文件檢視物件 （或 「 檢視 」） 代表一或多個 windows 在其中顯示文件資料物件。  
  
## 文件資料物件  
 文件資料物件是文字的資料表示文字緩衝區中。 它是 COM 物件來儲存文件文字和其他資訊、 處理文件的持續性，以及可讓多個資料檢視。 如需詳細資訊，請參閱  
  
 <xref:EnvDTE80.Window2.DocumentData%2A> 和 [文件視窗](../extensibility/internals/document-windows.md)。  
  
 自訂編輯器和設計工具，可以選擇使用 <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 物件或自己自訂的緩衝區。<xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> 簡化的內嵌模型會遵循標準編輯器、 支援多個檢視，並提供用來管理多個檢視的事件介面。  
  
## 文件檢視物件  
 這個視窗會顯示程式碼及其他文字稱為文件檢視。 當您建立編輯器時，您可以選擇在單一視窗中，文字會顯示單一檢視或多個檢視，顯示多個視窗中的文字。 您的選擇取決於您的應用程式。 例如，如果您需要編輯並存，您會選擇多個檢視。 每個檢視是整合式的開發環境 \(IDE\) 執行文件資料表 \(RDT\) 中的項目相關聯。 檢視 windows 屬於任何專案或 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 物件。  
  
 如果您的編輯器支援多個檢視的文件資料物件，則您的文件資料和文件檢視物件必須是不同。 否則，它們可以群組在一起。 如需詳細資訊，請參閱[支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)。  
  
 IDE 會通知檢視有關事件 （例如，包含文件方案已關閉） 的文件中執行表格的每個項目相符的項目識別碼 （識別碼）。 如需詳細資訊，請參閱[執行中的文件表格](../extensibility/internals/running-document-table.md)。  
  
 有兩個選項，建立自訂編輯器的檢視。 其中一個是就地啟用模型中，檢視放置在視窗中使用 ActiveX 控制項或文件資料物件。 第二個是簡化的內嵌模型，檢視由裝載 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 和 <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> 實作來處理視窗命令。 就地啟用模型的相關資訊，請參閱 [就地啟動](../misc/in-place-activation.md)。 簡化的內嵌模型的相關資訊，請參閱 [簡化的嵌入](../extensibility/simplified-embedding.md)。  
  
## 請參閱  
 [支援多個文件檢視](../extensibility/supporting-multiple-document-views.md)   
 [簡化的嵌入](../extensibility/simplified-embedding.md)   
 [如何︰ 附加至文件資料的檢視](../extensibility/how-to-attach-views-to-document-data.md)   
 [文件鎖定持有者管理](../extensibility/document-lock-holder-management.md)   
 [單一和多重\] 索引標籤檢視](../Topic/Single%20and%20Multi-tab%20Views.md)   
 [儲存的標準文件](../extensibility/internals/saving-a-standard-document.md)   
 [持續性和執行文件資料表](../extensibility/internals/persistence-and-the-running-document-table.md)   
 [決定編輯器隨即會開啟專案中的檔案](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)   
 [編輯器 Factory](../extensibility/editor-factories.md)