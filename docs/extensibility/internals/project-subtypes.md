---
title: "專案子類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案 [Visual Studio SDK]，子型別"
  - "專案子類型 [Visual Studio SDK]"
ms.assetid: d235b47b-cf11-4d47-a63f-e33d9d16105d
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# 專案子類型
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

專案子類型可讓您自訂或 flavor 的專案系統的行為 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]。 自訂作業包括將其他資料儲存在專案檔案中加入或篩選中的項目 **加入新項目** 對話方塊中，控制如何偵錯和部署，組件會和擴充專案 **屬性頁** 對話方塊。 VSPackages 實作使用 COM 彙總的專案子類型。  
  
> [!NOTE]
>  Visual c \+ \+ 專案系統不支援專案子類型。[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 本身會使用專案的子型別實作 SQL Server 和智慧型裝置專案。  
  
## 在本節中  
 [專案的子型別設計](../../extensibility/internals/project-subtypes-design.md)  
 描述專案子類型的概念。  
  
 [專案子類型的初始化順序](../../extensibility/internals/initialization-sequence-of-project-subtypes.md)  
 描述程式設計專案子型別初始設定順序，由 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 環境。  
  
 [屬性和方法的擴充專案子類型](../../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)  
 提供功能和最常使用的專案子型別擴充方法的詳細的的說明。  
  
 [在 MSBuild 專案檔案中保存的資料](../../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)  
 描述如何將保存在專案檔中的資料，以及如何使用 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistXMLFragment> 跨專案的子型別彙總層級維護專案檔案中的資料。  
  
 [專案屬性的使用者介面](../../extensibility/internals/project-property-user-interface.md)  
 描述如何專案子類型可以修改專案 **屬性頁** 對話方塊。  
  
 [擴充基底專案物件的模型](../../extensibility/internals/extending-the-object-model-of-the-base-project.md)  
 提供有關專案子類型如何擴充 automation 物件模型使用 Automation 擴充項的資訊。  
  
 [導致加入新項目對話方塊](../../extensibility/internals/contributing-to-the-add-new-item-dialog-box.md)  
 描述如何將項目加入 **加入新項目** 對話方塊。  
  
 [將資料儲存在專案檔](../../extensibility/saving-data-in-project-files.md)  
 說明如何儲存和使用管理套件架構 \(MPF\) 擷取專案檔中的子型別特定資料專案子類型。  
  
 [處理特製化部署](../../extensibility/internals/handling-specialized-deployment.md)  
 說明如何專案子類型時，可以藉由實作提供特定的部署行為 <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> 介面。  
  
 [加入和移除屬性頁](../../extensibility/adding-and-removing-property-pages.md)  
 描述加入和移除專案設計工具中的屬性頁。  
  
## 相關章節  
 [專案類型](../../extensibility/internals/project-types.md)  
 提供主題詳細說明連結 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 專案。