---
title: "新增目錄來加入新項目對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "加入新項目] 對話方塊中，擴充"
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# 新增目錄來加入新項目對話方塊
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

下列程式碼範例示範如何註冊一組新的目錄 **加入新項目** 對話方塊。 目錄 **加入新項目** ] 對話方塊中各有不同的每個專案。 因此，目錄下的專案子機碼，位於 \< HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects > 註冊︰  
  
## <a name="the-registry-script"></a>登錄指令碼  
  
```  
NoRemove Projects  
{  
  NoRemove %GUID_Project%  
  {  
    NoRemove AddItemTemplates  
    {  
      NoRemove TemplateDirs  
      {  
        ForceRemove %CLSID_Package%  
        {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
          {  
            val TemplatesDir = s '%Template_Path%'     
            val SortPriority = d 2000  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
 Template_Path 值會指定包含專案範本之目錄的完整路徑。 .Vsz 檔案或要複製的典型的範本檔案，可以使用這些範本。  
  
 SortPriority 值指定排序的優先順序。  
  
## <a name="adding-items-to-an-existing-project"></a>將項目加入至現有的專案  
 您也可以新增項目至現有的專案。 例如，對於 [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 專案中，您可以將項目加入 \< 根>files\microsoft Visual Studio \VC#\CSharpProjectItems\LocalProjectItems 資料夾。 在此情況下 `%GUID_Project%` 是 C# 專案 ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}) 的 GUID。  
  
 您也可以擴充現有的專案，以程式設計方式編寫專案的子型別。 與專案的子型別，您可以擴充專案，而不需要撰寫新的專案類型。 如需專案子類型的詳細資訊，請參閱 [專案子類型](../../extensibility/internals/project-subtypes.md)。  
  
## <a name="see-also"></a>請參閱  
 [註冊專案和項目範本](../../extensibility/internals/registering-project-and-item-templates.md)   
 [加入項目來加入新項目對話方塊](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [將目錄加入至新的 [專案] 對話方塊](../Topic/Adding%20Directories%20to%20the%20New%20Project%20Dialog%20Box.md)