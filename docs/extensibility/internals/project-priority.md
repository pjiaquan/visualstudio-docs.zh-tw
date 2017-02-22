---
title: "專案的優先順序 | Microsoft Docs"
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
  - "專案 [Visual Studio SDK]，開啟項目"
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# 專案的優先順序
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

專案項目通常是方案中只有一個專案的成員。  因此，IDE 可以輕易地判斷哪一個專案用來開啟項目中。  不過，如果某個項目是屬於一個以上的專案，IDE 會使用優先順序的架構來決定最佳專案以供開啟該項目。  
  
 下列清單會顯示專案優先順序的架構：  
  
-   IDE 呼叫<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A>方法，以判斷文件是否屬於該專案的方案中每一專案。  
  
-   如果文件是專案的成員，專案回應優先順序的專案指派來執行其該文件的處理。  比方說，一個語言專案會以高的優先順序，其語言原始程式檔的回應，但會以較低的優先順序無法辨識的檔案類型無法用做為建置程序的一部分。  
  
-   文件提供自訂的專案專用編輯器或設計工具的專案也會獲得較高的優先順序。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>列舉型別提供的文件的優先順序值。  
  
-   指定最高優先權的專案都可以開啟文件的內容。  如果兩個專案都傳回相同的優先權值，使用中的專案時，偏好。  如果方案中的任何專案不回應它可以開啟文件，IDE 會將文件放在其他檔案專案中。  如需詳細資訊，請參閱 [其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)。  
  
## 請參閱  
 [其他檔案專案](../../extensibility/internals/miscellaneous-files-project.md)   
 [如何: 開啟編輯器開啟的文件](../../extensibility/how-to-open-editors-for-open-documents.md)   
 [加入專案和專案項目範本](../../extensibility/internals/adding-project-and-project-item-templates.md)