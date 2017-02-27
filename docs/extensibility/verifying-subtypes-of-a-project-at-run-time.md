---
title: "在執行階段驗證專案的子類型 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "專案子類型"
  - "請檢查子類型"
ms.assetid: b87780ec-36a3-4e9a-9ee2-7abdc26db739
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# 在執行階段驗證專案的子類型
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

自訂專案子類型而定的 VSPackage 應包含子類型，讓它可以失敗適宜子型別是否不存在的邏輯來尋找。 下列程序示範如何確認有指定的子型別。  
  
### 若要確認有子型別  
  
1.  從專案和方案物件，以取得專案階層架構 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> VSPackage 中加入下列程式碼的物件。  
  
    ```  
    EnvDTE.DTE dte;  
    dte = (EnvDTE.DTE)Package.GetGlobalService(typeof(EnvDTE.DTE));  
  
    EnvDTE.Project project;  
    project = dte.Solution.Projects.Item(1);  
  
    IVsSolution solution;  
    solution = (IVsSolution)Package.GetGlobalService(typeof(SVsSolution));  
  
    IVsHierarchy hierarchy;  
    hierarchy = solution.GetProjectOfUniqueName(project.UniqueName);  
  
    ```  
  
2.  轉型階層 <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected> 介面。  
  
    ```  
    IVsAggregatableProjectCorrected AP;  
    AP = hierarchy as IVsAggregatableProjectCorrected;  
  
    ```  
  
3.  取得叫用的專案類型的 Guid 清單 <xref:Microsoft.VisualStudio.Shell.Flavor.IVsAggregatableProjectCorrected.GetAggregateProjectTypeGuids%2A>。  
  
    ```  
    string projTypeGuids = AP.GetAggregateProjectTypeGuids().ToUpper();  
  
    ```  
  
4.  檢查指定的子類型的 GUID 清單。  
  
    ```  
    // Replace the string "MyGUID" with the GUID of the subtype.  
    string guidMySubtype = "MyGUID";  
    if (projTypeGuids.IndexOf(guidMySubtype) > 0)  
    {  
        // The specified subtype is present.  
    }  
    ```  
  
## 請參閱  
 [專案子類型](../extensibility/internals/project-subtypes.md)   
 [專案的子型別設計](../extensibility/internals/project-subtypes-design.md)   
 [屬性和方法的擴充專案子類型](../extensibility/internals/properties-and-methods-extended-by-project-subtypes.md)