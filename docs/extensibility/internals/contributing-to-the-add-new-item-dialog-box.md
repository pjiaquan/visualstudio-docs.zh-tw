---
title: "導致加入新項目對話方塊 | Microsoft Docs"
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
  - "加入新項目] 對話方塊，導致"
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# 導致加入新項目對話方塊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

專案子類型可提供完整的新目錄的項目**加入新項目**註冊\] 對話方塊**加入項目**下的 \[範本`Projects`登錄子機碼。  
  
## 將登錄加入新項目範本  
 這個區段位於**HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Projects**在登錄中。  下列的登錄項目假設[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案彙總由假設性的專案子類型。  項目[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案如下所示。  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 `AddItemTemplates\TemplateDirs`子機碼包含與項目可以讓目錄路徑的登錄項目**加入新項目**會放在對話方塊中。  
  
 環境會自動載入所有的`AddItemTemplates`下的資料`Projects`登錄子機碼。  這可包括基底專案實作的資料，以及供特定專案子類型的資料。  每個專案的子型別由專案類型`GUID`。  專案子型別可以指定一組替代`Add Item`範本適用於特定的 flavored 的專案的執行個體支援`VSHPROPID_ AddItemTemplatesGuid`列舉型別從<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2>在<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>實作以傳回專案子類型的 GUID 值。  如果`VSHPROPID_AddItemTemplatesGuid`未指定屬性，基底使用 GUID 的專案。  
  
 您可以篩選中的項目**加入新項目**對話方塊中的，藉由實作<xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>專案子類型彙總物件上的介面。  比方說，實作方式，是彙總的資料庫專案的專案子類型[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]專案，可以篩選[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]特定項目從**加入新項目** ，請實作篩選，然後在對話方塊開啟，可以加入資料庫專案的特定項目支援`VSHPROPID_ AddItemTemplatesGuid`在<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>。  如需有關篩選，並加入項目至**加入新項目**對話方塊中，請參閱[加入項目來加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [物件，通常會用來擴充專案的 Catid](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)