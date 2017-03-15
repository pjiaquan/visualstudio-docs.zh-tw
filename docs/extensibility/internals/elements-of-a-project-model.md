---
title: "專案模型的項目 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案 [Visual Studio SDK]，實作考量"
  - "專案模型"
  - "專案 [Visual Studio SDK]，項目"
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
caps.latest.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 18
---
# 專案模型的項目
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

介面和實作中的所有專案的[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]共用基本結構： 您的專案類型的專案模型。  在您的專案模型中，也就是您正在開發的 VSPackage，您可以建立符合您的設計決策，並提供 IDE 的全域功能一起工作的物件。  雖然您控制如何保存專案項目，例如，您並不會控制檔案都必須保存的通知。  當使用者將焦點放在開啟的專案項目，並選擇**儲存**的**檔案**上的功能表[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]功能表列，您的專案型別程式碼必須攔截從 IDE 命令、 保存檔案，和傳送告知對應至 IDE 檔案且不能變更。  
  
 您的 VSPackage 會與透過服務提供對 IDE 介面存取 IDE 互動。  比方說，透過特定的服務監視器\] 及 \[路由命令也會提供在專案中所做的選取項目的內容資訊。  所提供的服務需要您 VSPackage 的所有通用的 IDE 功能。  如需有關服務的詳細資訊，請參閱[如何: 取得服務](../Topic/How%20to:%20Get%20a%20Service.md)。  
  
 其他考量事項：  
  
-   單一專案模型都包含一個以上的專案類型。  
  
-   專案類型和伴隨的專案工廠，則會與 Guid 一起獨立地登錄。  
  
-   每個專案必須有範本檔案或精靈，以初始化新的專案檔案，當使用者建立新的專案，透過[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] UI。  例如， [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)]範本初始化什麼最後變得.vcproj 檔。  
  
 下圖顯示主要的介面、 服務及撰寫的典型的專案實作的物件。  您可以使用應用程式協助程式，這是 HierUtil7，來建立基礎的物件和其他程式重複使用。  如需有關 HierUtil7 應用程式協助程式的詳細資訊，請參閱[Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/zh-tw/a5c16a09-94a2-46ef-87b5-35b815e2f346)。  
  
 ![Visual Studio 專案模型圖形](../../extensibility/internals/media/vsprojectmodel.png "vsProjectModel")  
專案模型  
  
 如需有關介面，並列出在前一個圖表中，服務和其他選擇性的介面不會包含在圖表中的詳細資訊，請參閱[專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)。  
  
 專案可以支援命令，因此必須實作<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>參與命令傳送到指令內容 Guid 的介面。  
  
## 請參閱  
 [檢查清單︰ 建立新的專案類型](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Not in Build: Using HierUtil7 Project Classes to Implement a Project Type \(C\+\+\)](http://msdn.microsoft.com/zh-tw/a5c16a09-94a2-46ef-87b5-35b815e2f346)   
 [專案模型的核心元件](../../extensibility/internals/project-model-core-components.md)   
 [使用專案 Factory 建立專案](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)   
 [如何: 取得服務](../Topic/How%20to:%20Get%20a%20Service.md)   
 [建立專案類型](../../extensibility/internals/creating-project-types.md)