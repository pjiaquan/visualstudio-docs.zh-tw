---
title: "將屬性加入至專案項目 | Microsoft Docs"
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
  - "屬性 [Visual Studio]，加入至專案項目"
ms.assetid: 404a71d5-cce5-44e7-9eaf-d747c794fedb
caps.latest.revision: 4
caps.handback.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
---
# 將屬性加入至專案項目
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

這些方法<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.GetItemAttribute%2A>和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>取得和設定的專案項目的屬性值。  SetItemAttribute 屬性時建立它並不存在，請將它加入至專案的項目中繼資料。  
  
## 將屬性加入至專案項目  
  
#### 若要將屬性加入至專案項目  
  
-   下列程式碼使用<xref:EnvDTE.DTE>自動化物件和<xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildPropertyStorage.SetItemAttribute%2A>方法，以將屬性加入至專案項目。  從專案項目名稱"program.cs"取得的專案項目識別碼。  屬性"MyAttribute"是加入至這個專案項目，並賦予"MyValue"的值。  
  
    ```  
    EnvDTE.DTE dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
    EnvDTE.Project project = dte.Solution.Projects.Item(1);  
  
    string uniqueName = project.UniqueName;  
    IVsSolution solution =     (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
    IVsHierarchy hierarchy;  
    solution.GetProjectOfUniqueName(uniqueName, out hierarchy);  
    IVsBuildPropertyStorage buildPropertyStorage = hierarchy as IVsBuildPropertyStorage;  
    if (buildPropertyStorage != null)  
    {  
        uint itemId;  
        string fullPath =         (string)project.ProjectItems.Item("Program.cs").Properties.Item("FullPath").Value;  
        hierarchy.ParseCanonicalName(fullPath, out itemId);  
        buildPropertyStorage.SetItemAttribute(  
            itemId, "MyAttribute", "MyValue");  
    }  
  
    ```  
  
## 請參閱  
 [在 MSBuild 專案檔案中保存的資料](../extensibility/internals/persisting-data-in-the-msbuild-project-file.md)