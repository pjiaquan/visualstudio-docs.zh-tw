---
title: "將目錄加入至新的 [專案] 對話方塊 | Microsoft Docs"
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
  - "新增專案] 對話方塊擴充"
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# 將目錄加入至新的 [專案] 對話方塊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

當您建立新的專案類型時，您也可以註冊新的目錄，在**新的專案**用於顯示成範本\] 對話方塊。  下列程式碼範例說明如何註冊新的目錄，也就是一個節點。  在範例中，會登錄 VSPackage CLSID\_Package 所公開的範本。  因此，左下方**新的專案**對話方塊提供 \[加入\] 節點中，由 Folder\_Label\_ResID 資源的名稱。  這項資源是從 VSPackage 附屬 DLL 載入。  
  
 **資料夾**值代表的資料夾的 \[Folder\_Label\_ResID\] 節點會顯示在其下的 GUID。  在範例中，代表 GUID **其他專案** \] 資料夾中的 **專案類型** 的窗格 **新的專案**對話方塊。  如果**其他專案**值為不存在時，標籤會定位在頂部層級。  
  
 TemplatesDir 值會指定包含專案範本目錄的完整路徑。  這些檔案可以是.vsz 檔或是要複製的典型的範本檔案。  
  
 如果您指定 TemplatesLocalizedSubDir 時，它必須是字串的命名的 TemplatesDir 保存當地語系化的範本子目錄資源識別碼。  因為[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]載入字串資源的附屬 DLL 中如果有的話，每個附屬 DLL 可以包含不同的目錄名稱。SortPriority 值指定的排序優先順序。  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## 請參閱  
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [加入項目來加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [新增目錄來加入新項目對話方塊](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)